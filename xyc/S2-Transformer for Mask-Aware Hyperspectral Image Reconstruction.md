 1  S2-Transformer for Mask-Aware Hyperspectral Image Reconstruction +TPAMI刊物+2022提、2025修订完+链接：[2209.12075](https://arxiv.org/pdf/2209.12075)

基于掩膜感知的高光谱图像重建的S2-Transformer方法 TPAMI

2025/11/12 (阅读时间)



1.问题:  **卫星从太空拍摄**的农田照片，不仅能看清作物的形状，还能分析出每一片叶子的"健康密码"？

​        答：                  高光谱成像技术——它能捕捉肉眼看不到的光谱细节

2.高光谱成像技术

 近年来流行的"**快照压缩成像（SCI）**"技术，比如编码孔径快照光谱成像仪**（CASSI）**：能一次性把三维高光谱数据压缩成二维图像。



**关键问题：**

（1）**信息纠缠。**不同波长的空间细节被强行"挤"在一张图里

（2）**掩膜数据丢失。**掩膜会遮挡部分光线，被挡住的区域就像照片上的"黑洞"，原始信息没了，重建时很容易出错。



3. S2-Transformer：网络框架

<img width="1080" height="390" alt="image" src="https://github.com/user-attachments/assets/f66c1958-ba5d-48b3-bb30-03d0bf2feb7a" />

整个网络分为三部分：

- 特征提取器：用3×3卷积层把输入数据转换成特征向量
- S2-attn Transformer阶段：**核心**部分，通过**多个注意力块**处理空间和光谱信息

   **Spatial MSA**：在每个窗口的 M2M^2M2 个像素之间做自注意，抓长程空间关系；

  **Spectral MSA**：在每个窗口内的**通道/波段**之间做自注意，显式建模波段依赖；

两种组织方式：**顺序（Sequen-SS）\**或\**并行（Parall-SS）**

采用**并行**，因为在**精度更高**的同时**计算量更小**，且能让两类注意力更**独立、融合**更灵活。

<img width="301" height="33" alt="image" src="https://github.com/user-attachments/assets/2df9476c-767b-4cfd-ad2a-086476d7ceed" />


- 重建头： 3×3 卷积把处理好的特征转换回高光谱图像

而最关键的，就是中间的"并行空间光谱注意力"和"掩膜感知学习"两大绝技。



4.绝技一：并行注意力，同时抓牢空间和光谱细节

**空间注意力**像"近视眼"：能看清像素之间的联系，却看不清每个像素在不同波长下的变化

**光谱注意力**像"老花镜"：能分析波长规律，却抓不住精细的空间细节

<img width="1080" height="423" alt="image" src="https://github.com/user-attachments/assets/b313d85a-f80b-4c7e-b33b-26a206529be5" />


 LN（LayerNorm 预归一化）、MSA（多头自注意）、FFN（前馈层），以及“⊕”残差

**\**线性投影**回通道数，再残差 + FFN。这样两种注意力**互不干扰、再融合**



5.绝技二：掩膜感知学习，给"黑洞区域"开小灶

  **被掩膜遮挡**的区域重建难度大，但之前的**损失函数**对所有**像素"一碗水端平"**，导致这些区域总是拖后腿。
<img width="1063" height="433" alt="image" src="https://github.com/user-attachments/assets/89dd9625-c6be-4157-a694-f74214711340" />

它通过两步操作实现：


1. 先预训练模型，让它学会识别哪些是掩膜区域（通过拟合编码信号F'）ME
<img width="428" height="65" alt="image" src="https://github.com/user-attachments/assets/f630817b-1602-4ced-92d4-b755c4460dab" />

第一项让辅助头，当于得到一张“哪里难/被遮”的难度图，第二项是普通重建损失

   
2. 正式训练时，给掩膜区域的损失"加权重"，让模型更关注这些难修复的地方 MA

<img width="420" height="76" alt="image" src="https://github.com/user-attachments/assets/2ec46973-08b3-4c78-940b-21e02a1fb649" />

在被遮挡处，编码信号 F' 很弱 → 辅助头输出也小 → 分母小 → 权重大 → 更严惩这些像素,

在无遮挡处，F/信息足 一 分母大 一 额外惩罚趋近于 0，几乎不影响正常区域。

6.结果

不同波长重建结果对比

<img width="1080" height="464" alt="image" src="https://github.com/user-attachments/assets/98cd61f4-db36-4ea2-bdf6-beac24a5e3eb" />



7.**并行空间×光谱注意力**：去云同样存在**空间遮挡**与**跨波段不一致**（薄云、云影引起的光谱漂移）

**掩码感知训练**：把**云掩膜/云概率**当成“掩码”，给云区更高损失权重


ACA 当前偏“空间注意力”型


