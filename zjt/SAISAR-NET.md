# SAISAR-Net: A Robust Sequential Adjustment ISAR Image Classiﬁcation Network

本文提出了一种名为**SAISAR-Net（Sequential Adjustment ISAR Image Classification Network）**的深度学习网络，专用于处理和分类具有未知变形的ISAR序列图像 。


<img width="1071" height="524" alt="ScreenShot_2025-11-12_213841_315" src="https://github.com/user-attachments/assets/073cb4e5-e313-4124-995d-1f06366b89ac" />





### 1.1 总体架构概览

  SAISAR-Net 的输入是一个ISAR图像序列 $S \in \mathbb{R}^{F \times N_x \times N_y}$，其中 $F$ 是序列长度,Nx和Ny是图像尺寸（实验中为 $120 \times 120$）。

1. **全局调整**：首先，序列中的每一帧图像都经过一个共享参数的仿射变换网络，校正其旋转、平移和缩放。
2. **局部调整**：校正后的图像进入特征提取网络，通过可变形卷积层，对特征图进行像素级的微调，以适应局部结构变化。
3. **时序融合**：提取出的特征向量序列被送入Bi-LSTM，并结合注意力机制进行加权融合，最终输出分类标签 。



### 1.2 全局图像调整模块 (Global Image Adjustment)

该模块旨在模拟并逆转ISAR成像过程中的刚性几何形变。其数学基础是二维仿射变换。

#### 1.2.1 仿射变换原理

对于图像上的任意像素坐标 $(x^p, y^p)$，其变换后的新坐标 $(x_{at}^p, y_{at}^p)$ 由仿射矩阵 $\Theta_1$ 决定：

$$\begin{bmatrix} x_{at}^p \\ y_{at}^p \\ 1 \end{bmatrix} = \Theta_1 \begin{bmatrix} x^p \\ y^p \\ 1 \end{bmatrix} = \begin{bmatrix} a_1 & a_2 & a_3 \\ a_4 & a_5 & a_6 \end{bmatrix} \begin{bmatrix} x^p \\ y^p \\ 1 \end{bmatrix}$$

矩阵 $\Theta_1$ 包含了旋转 $\Theta_r$、缩放 $\Theta_s$ 和平移 $\Theta_t$ 的组合效应 1。SAISAR-Net 的任务是根据输入图像自动预测出这6个参数 $a_1, \dots, a_6$。

#### 1.2.2 网络结构设计：Lower ConvNet 与 Deformed Affine ConvNet

为了高效地估计仿射参数，作者设计了一个独特的结构，包含两个子网络：

- **Lower ConvNet（底层共享网络）**：这是一个由三层卷积-池化块组成的特征提取器。表I 1 显示，Stage 1 输出 $8 \times 56 \times 56$，Stage 2 输出 $16 \times 25 \times 25$，Stage 3 输出 $32 \times 9 \times 9$。**关键创新点**在于，这个Lower ConvNet的参数在全局调整模块和后续的局部调整模块之间是**完全共享**的。这种设计不仅减少了约32.5%的参数量（从690k减少到466k），还有效防止了过拟合，因为底层网络被迫学习对全局姿态估计和局部特征提取都通用的鲁棒特征 1。
- **Deformed Affine ConvNet**：这是专门用于回归仿射参数的分支。它接收Lower ConvNet的输出，经过两层可变形卷积（Deformable Convolution）和一个全连接层，最终输出 $2 \times 3$ 的参数矩阵 $\Theta_2$。**为何在此处使用可变形卷积？** 这是一个精妙的设计。由于ISAR图像的散射点可能会闪烁或移动，使用固定感受野的普通卷积难以稳定地捕捉目标的姿态特征。可变形卷积允许网络自适应地聚焦于那些位置相对稳定的强散射中心，从而提高参数估计的准确性 1。

#### 1.2.3 仿射重采样与反向传播

获得参数 $\Theta_2$ 后，网络对输入图像序列 $S$ 进行重采样。由于计算出的坐标 $(x_{at}^f, y_{at}^f)$ 通常是非整数，必须使用双线性插值（Bilinear Interpolation）来计算像素灰度。文献 1 详细推导了输出像素 $\hat{I}$ 对输入像素 $I$ 和坐标 $(x, y)$ 的偏导数：

$$\frac{\partial \hat{I}_{x_{at}, y_{at}}^f}{\partial x_{at}^f} = \sum_{i} \sum_{j} I_{i,j}^f \max(0, 1 - |y_{at}^f - j|) \cdot \text{sign}(\max(0, 1 - |x_{at}^f - i|))$$

这一可微性保证了误差可以通过分类损失函数一直反向传播到仿射参数预测网络，从而实现无监督的几何校正学习。

### 1.3 局部图像调整模块 (Local Image Adjustment)

全局调整无法解决非刚性的局部扭曲。局部模块通过在特征图层面引入偏移量来解决这一问题。

#### 1.3.1 可变形卷积机制

普通卷积在特征图上的采样网格是固定的（如 $3 \times 3$ 方阵）。可变形卷积则为每个采样点引入了一个可学习的二维偏移量 $\Delta \mathbf{p}_n$。输出特征图上位置 $\mathbf{p}_0$ 的值计算如下：

$$y(\mathbf{p}_0) = \sum_{\mathbf{p}_n \in \mathcal{R}} w(\mathbf{p}_n) \cdot x(\mathbf{p}_0 + \mathbf{p}_n + \Delta \mathbf{p}_n)$$

其中 $\Delta \mathbf{p}_n$ 由一个旁路卷积层（Offset Generator）从输入特征图中学习得到 1。

#### 1.3.2 Deformed Shrink ConvNet

该模块同样利用共享的 Lower ConvNet 提取的特征，然后接入 **Deformed Shrink ConvNet**。顾名思义，该网络不仅进行形变调整，还负责特征的降维（Shrink）。它包含两层卷积（64通道和128通道），均采用可变形卷积核。这种设计使得网络能够针对ISAR图像中因微小转动引起的散射点漂移进行补偿，确保提取的特征在空间结构上的一致性。最终，通过全连接层，每一帧图像被压缩为一个特征向量，供序列模块使用。

### 1.4 序列特征融合：注意力增强 Bi-LSTM

经过前两个模块，图像序列被转化为了一组特征向量序列。为了捕捉时序演变规律并剔除劣质帧的影响，SAISAR-Net 采用了注意力增强的 Bi-LSTM。

#### 1.4.1 双向长短时记忆网络

Bi-LSTM 包含两个独立的LSTM层：一个按时间正序处理（Forward），捕捉过去的信息；另一个按时间逆序处理（Backward），捕捉未来的上下文信息 1。对于ISAR成像，未来的帧（即不同角度的观测）往往能辅助判断当前帧的模糊特征。每个时刻 $t$ 的输出是前向隐状态 $\vec{\mathbf{h}}_t$ 和后向隐状态 $\overleftarrow{\mathbf{h}}_t$ 的拼接。

#### 1.4.2 加性注意力机制 (Additive Attention)

为了解决长序列中信息权重分配不均的问题，作者引入了加性注意力。将 Bi-LSTM 的输出序列定义为 Key 和 Value。注意力分数 $\alpha_t$ 的计算公式为：

$$\text{Score}(\text{Key}, \text{Que}) = \mathbf{v}^T \tanh(W_1 [\text{Key}; \text{Que}])^T$$

$$\alpha_t = \text{softmax}(\text{Score})$$




## 









