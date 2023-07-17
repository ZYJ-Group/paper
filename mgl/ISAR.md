#  ISAR Image Generation
## 1篇 Ruo-Yi Zhou (Keywords:ISAR,ATR,GANs)
- Key laboratory for Information Science of Electromagnetic Waves (MoE), School of Information Science and 
  Technology, Fudan University, Shanghai, China
### 1 ISAR Images Generation Via Generative Adversarial Networks (IEEE International Symposium on Geoscience and Remote Sensing (IGARSS),2021)  [paper](images/ISAR_Images_Generation_Via_Generative_Adversarial_Networks.pdf)
- 2023/07/07
#### conslusion by mgl 当前智能目标识别任务面临的挑战之一是缺乏样本，特别是在逆合成孔径雷达(ISAR)图像理解方面。近年来发展起来的识别算法，特别是基于深度学习方法的识别算法，在很大程度上依赖于现有的训练数据。然而，据我们所知，目前还没有开源的实用ISAR数据集能够覆盖全方面角度。本文提出了一种ISAR目标生成网络，用于多向ISAR图像的生成。利用双向分析射线追踪(BART)方法，生成了六种飞机的模拟ISAR数据集。然后，利用模拟的ISAR数据集对所提出的生成网络进行训练。 使用结构相似度(SSIM)来评估所提出网络的性能。实验结果表明，生成的目标与真实ISAR图像非常接近，生成的飞机ISAR图像与真实ISAR图像之间的SSIM大于0.7;所提出的生成网络能够较好地生成缺失角度下的高分辨率ISAR图像，且图像与真实图像基本一致。

![流程图](images/ISAR-1.png)

##  廖淮璋 （关键词：图像生成；逆合成孔径雷达（ISAR）图像生成；循环对抗生成网络）
- 国防科技大学电子科学学院，长沙，中国
### 2基于物理先验的空间目标光学-ISAR 图像跨域生成  [paper](images/R23063_P_editing.pdf)
#### conslusion by mgl  在较大物理特性差异的条件下，创建一个通用模型去解决光学图像域到ISAR图像域的图像转换生成问题，为基于深度学习的空天目标检测识别算法的应用提供数据支撑。  基于深度学习的识别检测模型通常依赖于大量的训练样本以得到优秀的性能保证。然而在实际应用中，空间目标的ISAR图像往往不易获取且成本高昂，因此限制了现有的前沿深度学习方法在ISAR图像处理中的应用；现有的光学图像翻译方法难以兼顾空天目标在雷达波下的物理特征（散射点强度、分布与强度变化方向等），因此对ISAR图像生成的效果较差。通过图像翻译技术从空间目标（如飞机、卫星）的光学图像生成对应ISAR图像，解决空间目标的ISAR图像往往不易获取且成本高昂的问题,提出了一种基于物理先验的循环生成对抗网络（Physical Domain Prior CycleGAN, PDP-CycleGAN）以学习ISAR图像中的物理域特征。解决存在显著差异物理特征的不同图像域的图像翻译问题。通过构建基于特征隐空间的拉格朗日函数损失函数，使得生成模型能够在训练中学习ISAR图像的散射点分布特征。采用尺度不变特征变换（Scale Invariant Feature Transform，SIFT）算法提取ISAR图像中的散射点强度、分布与散射点强度变化方向，并基于此构建ISAR图像域的物理先验一致性。通过一致性的构建，PDP-CycleGAN能够学习ISAR图像域与光学图像域的可逆映射，从而获取生成空间目标的ISAR图像的生成器。将本文所提PDP-CycleGAN方法分别在三个角度（非配对图像翻译，方位角变换下空间目标翻译,陌生目标ISAR 图像翻译 ）与传统主流方法CycleGAN、UNIT进行对比，并通过初始分数(Inception Score,IS)与多尺度结构相似度指数（Multi-scale Structural Similarity,MS-SSIM)对生成的ISAR图像进行定量评估。实验结果表明：PDP-CycleGAN具有最佳的性能，其在散射点分布、强度等特征上与真实的ISAR图像保持一致。
![流程图](images/R23063_1.jpg)
