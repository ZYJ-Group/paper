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
![Image]([https://raw.githubusercontent.com/Gladysid/Images-blog/master/IE-box-pic.png](https://github.com/ZYJ-Group/paper/blob/28bfe3ce7a88afa9298e8210f62061c27e3587d7/lcw/image/VIPS-2.png))


