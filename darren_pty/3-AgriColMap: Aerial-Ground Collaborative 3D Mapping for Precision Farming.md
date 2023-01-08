研究领域：三维重建
-----  
题目：Aerial-Ground Collaborative 3D Mapping for Precision Farming
-----  
原文链接：https://github.com/ZYJ-Group/darren_pty/tree/main/darren_pty/0-paper  
-----  

### 一、简介：
  - 目的：将uav和ugv结合建立和更新共同地图用于精准农业。
  - 挑战：
     - 1、建立和更新一个共同的实地地图，使用不同类型的机器人构建的地图在大小、分辨率和比例尺上表现出差异
     - 2、相关的地理位置数据可能不准确和有偏差
     - 3、在农业环境中发现的```视觉外观和几何结构的重复性```使得传统的地图合并技术无效

     - ![](https://github.com/ZYJ-Group/darren_pty/blob/main/darren_pty/pic(Ninth%20week)/40.png)

  - 作者提出的新的地图配准AgriColMap步骤：
     - 1、利用了基于网格的多模式环境表示，其中包括植被指数地图和数字表面模型；
     - 2、将UAV和UGV地图之间的数据关联问题转换为多模态、大位移密集光流估计；
     - 3、使用投票方案选择的主导相干流用作点对点对应以推断图之间的初步非刚性对准；
     - 4、通过仅利用配准图的有意义部分来执行最终细化。



## 注：
图像配准：是用来获取图像的空间位置信息,通过某种空间变化对齐两张图像或者多张图像,对齐可以使图像在几何空间中存在一一对应的关系。

图像配准的方法根据图像形变分为刚性配准和非刚性配准；

刚性配准方法是对图像进行线性配准；

非刚性图像配准是寻找图像之间的空间非线性变换,其中待配准图像之间的形变方向和大小不确定度较高。

非刚性图像配准的方法主要包括基于特征图像配准和基于灰度图像配准；

基于特征图像配准的方法是寻找图像中特征点(点、线和轮廓)之间的对应关系,该方法的配准速度较快,缺点为特征难以提取和图像配准精度较低。

基于灰度图像配准的方法是直接利用图像的灰度值,该方法能够使图像的所有信息都用在图像配准的过程中,可在特征提取的过程中避免人工干涉。


### 二、AgriColMap具体步骤：
- 1、UGV和UAV都使用从其机载摄像机收集的数据生成耕地的彩色点云MA和MG；
- 2、通过仿射变换F将UGV子地图（红色矩形区域）配准到UAV航空地图（蓝色矩形区域）中;
- 3、并考虑到可能的比例差异，从而准确地合并这些地图(```目标是找到转换F：R3 →R3，允许它们精确对齐```)。
 ![](https://github.com/ZYJ-Group/darren_pty/blob/main/darren_pty/pic(Ninth%20week)/41.png)

#### 2.1由UAV和UGV收集的输入彩色点云 
(1)无人机数据集是由1200万像素彩色摄像机的DJI Mavic Pro无人机获得的，无人地面车数据集是通过用手移动同一台摄像机获得的，摄像机具有前视视角，模拟了地面机器人的数据采集。

(2)使用专业摄影测量软件套件Pix4Dmapper将采集的图像转换为3D彩色点。

![](https://github.com/ZYJ-Group/darren_pty/blob/main/darren_pty/pic(Ninth%20week)/42.png)


#### 2.2GPS和AHRS提供的初始噪声和偏差刚性对准
GPS和AHRS传感器为两点云之间的刚性转换提供了初步猜测.
通过计算一个“密集流”来估计mA，G，给定GPS和AHRS提供的地图之间的初始噪声校准，将MA中的点与MG中的点联系起来。

![](https://github.com/ZYJ-Group/darren_pty/blob/main/darren_pty/pic(Ninth%20week)/43.png)



#### 重建效果
甜菜

![](https://github.com/ZYJ-Group/darren_pty/blob/main/darren_pty/pic(Ninth%20week)/49.png)

大豆：

![](https://github.com/ZYJ-Group/darren_pty/blob/main/darren_pty/pic(Ninth%20week)/50.png)

冬麦

![](https://github.com/ZYJ-Group/darren_pty/blob/main/darren_pty/pic(Ninth%20week)/51.png)

