Automatic Driving Technique
=====

Automatic Driving Perception
-----  
## VIPS: Real-Time Perception Fusion for Infrastructure-Assisted Autonomous Driving (ICRA 2022)
### 原文链接：https://yanzhenyu.com/assets/pdf/VIPS-MobiCom22.pdf
### 视频链接：https://youtu.be/zW4oi_EWOu0
#### 简介：
  - 创新点：提出车辆-基础设施融合感知方案，精准对齐多源数据，扩展了车辆的感知范围。
  - 步骤：
    - 1、基础设施和车辆上的感知方案分别检测车辆以及行人；
    - 2、跟踪物体的特性和运动速度，基于此信息将基础设施中的信息帧与车辆的信息帧之间进行时间校准；
    - 3、VIPS构建两个多亲和图，利用高效的图匹配算法识别两个视图中的共同可见对象；
    - 4、VIPS通过查找基于共可见对象的转换，将所有对象对齐至车辆视图中。
  - 优点：
    - 1、VIPS有效地利用了基础设施的计算/通信资源，因为只有少量的检测结果会广播给所有过往车辆。
    - 2、VIPS利用了动态对象从不同角度的空间和语义一致性，实现了精确的实施对齐，而不依赖于车辆的高精度定位；
    - 3、VIPS利用了运动物体的特性，有连续性的信息表示，减少了基础设施以及车辆的算力要求。
   
    <div align=center>
    <img width="500" alt="image" src="https://github.com/ZYJ-Group/paper/blob/662e1fc595d9f66c673fd21ac38e8a1f5f2b75fc/lcw/image/VIPS-2.png">

    <img width="700" alt="image" src="https://github.com/ZYJ-Group/paper/blob/662e1fc595d9f66c673fd21ac38e8a1f5f2b75fc/lcw/image/VIPS-3.png">
    <img width="500" alt="image" src="https://github.com/ZYJ-Group/paper/blob/662e1fc595d9f66c673fd21ac38e8a1f5f2b75fc/lcw/image/VIPS-7.png">
    </div>

SLAM
-----
## Teed Z, Lipson L, Deng J. Deep Patch Visual Odometry[J]. arXiv preprint arXiv:2208.04726, 2022.
### 原文链接：https://arxiv.org/pdf/2208.04726.pdf
#### 简介：
  - 创新点：提出一种新的单目视觉里程计深度学习系统，将基于patch关联、迭代更新、可微BA集成于单一体系结构中，实现了低算力高性能的定位与建图功能。（在一个RTX-3090 GPU上仅使用4GB内存，以2 -5倍的实时速度运行）
  - 步骤：
    - 1、patch提取；（此处的patch为关键帧中的局部窗口）  
    使用一对残差网络从输入图像中提取特征：一个网络提取匹配特征，另一个网络提取上下文特征。  
    每个网络的第一层是一个跨步2的7 × 7卷积，后面是两个1/2分辨率的剩余块(维64)和两个1/4分辨率的剩余块(维128)，这样最终的特征映射是输入分辨率的1/4。  
    匹配网络和上下文网络的结构是相同的，除了匹配网络使用实例规格化，而上下文网络不使用规格化。  
    并且其使用一个四乘四步滤波器对匹配特征进行平均池化，构建了一个两级特征金字塔，为每一帧存储匹配的特征。  
    此外，其还从匹配和上下文特征映射中提取补丁，并且在随机抽取斑块质心的基础上，采用双线性插值方法进行特征提取。  
    - 2、更新器；（通过循环神经网络跟踪这些patch，并进行迭代BA优化）
    <div align=center>
    <img width="700" alt="image" src="https://github.com/ZYJ-Group/paper/blob/main/lcw/image/DPVO-2.png">
    </div>
  - 优点：
    - 实现了轻量级，但是在实际环境中，是否鲁棒还得验证一下。   
    <div align=center>
    <img width="500" alt="image" src="https://github.com/ZYJ-Group/paper/blob/main/lcw/image/DPVO-1.png">
    <img width="700" alt="image" src="https://github.com/ZYJ-Group/paper/blob/main/lcw/image/DPVO-3.png">
    <img width="500" alt="image" src="https://github.com/ZYJ-Group/paper/blob/main/lcw/image/DPVO-4.png">
    </div>
