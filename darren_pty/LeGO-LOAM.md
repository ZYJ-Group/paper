3D Lidar To SLAM(大方向)
-----  
LeGO-LOAM: Lightweight and Ground-Optimized Lidar Odometry and Mapping on Variable Terrain(标题)
-----  
- Tixiao Shan and Brendan Englot(作者)
- IROS 2018(刊物)
- 原文链接：https://github.com/RobustFieldAutonomyLab/LeGO-LOAM 

### 简介：
  - 创新点：提出一种轻型和基于地面优化的激光雷达里程计和建图的方法LeGO-LOAM，用于地面车辆的实时六自由度姿态估计。
    - 1、LeGO-LOAM是轻量的，它可以在低功耗嵌入式系统上实现实时姿态估计
    - 2、LeGO-LOAM是基于地面优化的，它在分割和优化步骤中利用了地面
  - 步骤：
     - 1、首先应用点云分割来滤除噪声
     - 2、然后进行特征提取以获得不同的平面和边缘特征
     - 3、然后利用平面和边缘特征采用了两步Levenberg-Marquardt优化方法，来求解连续扫描中六自由度变换的不同分量
  - 效果： LeGO-LOAM在降低计算开支的情况下达到了与LOAM类似或更好的精度
 
  - 框架：
  
  ![](https://img-blog.csdnimg.cn/7f4559a99c98438caca37e237bedad35.png)
