# 研读论文汇总

## 一、点云配准(Cloud Registration)
### 1、跨源点云配准
#### 1.1 基于传统优化方法
- [1-综述](https://github.com/Darren-pty/Research/blob/main/Learning%20of%20way/Semester/MiddleStation/4-1.md)
- [2-HybridFusion: LiDAR and Vision Cross-Source Point Cloud Fusion](https://github.com/Darren-pty/Research/blob/main/Learning%20of%20way/Semester/picture/53.png)
- [3-AgriColMap: Aerial-Ground Collaborative 3D Mapping for Precision Farming](https://github.com/ZJUT-IoCS-MAS/darren_pty/blob/main/2-Second%20semester/2023-2-16.png)
- [4-Point Cloud Registration Based on 1-point RANSAC and Scale-annealing Biweight Estimation](https://github.com/Darren-pty/Research/blob/main/paper/2-paper%20note/2-cloud%20registration/3-Point%20Cloud%20Registration%20Based%20on%201-point%C2%A0RANSAC%20and%20Scale-annealing%20Biweight%20Estimation%C2%A0.md)



#### 1.2 深度神经网络方法
- [7-Learning multiview 3D point cloud registration](https://blog.csdn.net/peng_258/article/details/130373356?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22130373356%22%2C%22source%22%3A%22peng_258%22%7D)



### 2、同源 激光雷达点云配准
#### 1.1 深度神经网络方法
- [17-JoKDNet: A joint keypoint detection and description network for large-scale
outdoor TLS point clouds registration](https://blog.csdn.net/peng_258/article/details/132538446?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132538446%22%2C%22source%22%3A%22peng_258%22%7D)

- [20-APR: Online Distant Point Cloud Registration through Aggregated Point Cloud Reconstruction](https://blog.csdn.net/peng_258/article/details/132639225?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132639225%22%2C%22source%22%3A%22peng_258%22%7D)
> 两个远距离车辆上面的同源雷达 对视野中 共存物体点云 对齐 

- [21-RoReg: Pairwise Point Cloud Registration With Oriented Descriptors and Local Rotations](https://blog.csdn.net/peng_258/article/details/132579689?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132579689%22%2C%22source%22%3A%22peng_258%22%7D)
> 带方向的描述子 + 局部旋转 实现室内外点云配准

- [22-PREDATOR: Registration of 3D Point Clouds with Low Overlap](https://blog.csdn.net/peng_258/article/details/132942481?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132942481%22%2C%22source%22%3A%22peng_258%22%7D)
> 低重叠率点云配准 backbone=KPConv,使用了transformer self-attention   2021 CVPR

- [23-CoFiNet: Reliable Coarse-to-fine Correspondences for Robust Point Cloud Registration](https://blog.csdn.net/peng_258/article/details/133189505?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22133189505%22%2C%22source%22%3A%22peng_258%22%7D)
> NIPS 2021 使用了transformer self-attention 性能高于predator和D3feat


--- 

#### 1.2 基于传统优化方法
- [18-Multisource forest point cloud registration with semantic-guided keypointsand robust RANSAC](https://blog.csdn.net/peng_258/article/details/132571460?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132571460%22%2C%22source%22%3A%22peng_258%22%7D)
> 针对 森林 的空地同源配准



---
--- 




## 二、三维重建
- [5-Toward Cooperative 3D Object Reconstruction with Multi-agent](https://github.com/ZYJ-Group/paper/blob/main/darren_pty/2-Toward%20Cooperative%203D%20Object%20Reconstruction%20with%20Multi-agent.md)







## 三、SLAM
### 3.1 lidar 
- [6-LeGO-LOAM](https://github.com/ZYJ-Group/paper/blob/main/darren_pty/1-LeGO-LOAM.md)

- [13-FAST-LIO](https://blog.csdn.net/peng_258/article/details/132320757?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132320757%22%2C%22source%22%3A%22peng_258%22%7D)
> 香港大学星火实验室






## 四、点云标定(Cloud Calibration)

### 1、激光雷达-相机标定 
- [8-Calib-Anything: Zero-training LiDAR-Camera Extrinsic Calibration Method Using Segment Anything](https://blog.csdn.net/peng_258/article/details/131326403?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22131326403%22%2C%22source%22%3A%22peng_258%22%7D)





## 五、语义分割
### 5.1 3D
- [9-Segment Anything in 3D with NeRFs](https://blog.csdn.net/peng_258/article/details/131367841?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22131367841%22%2C%22source%22%3A%22peng_258%22%7D)


- [10-SQN: Weakly-Supervised SemanticSegmentation of Large-Scale 3D Point Clouds](https://blog.csdn.net/peng_258/article/details/131753619?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22131753619%22%2C%22source%22%3A%22peng_258%22%7D)
> 弱监督语义分割：少量标注实现较高精度3D语义分割
--- 

#### 5.1.1 城市级室外RGB语义分割
- [11-Efficient Urban-scale Point Clouds Segmentation with BEV Projection](https://blog.csdn.net/peng_258/article/details/132149629?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132149629%22%2C%22source%22%3A%22peng_258%22%7D)
> 基于投影的方法, 投影思路可以用于3D点云转2D图片，且有相关代码可借鉴

---
- [12-RandLA-Net: Efﬁcient Semantic Segmentation of Large-Scale Point Clouds](https://blog.csdn.net/peng_258/article/details/132085815?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132085815%22%2C%22source%22%3A%22peng_258%22%7D)
> 基于点的方法(直接处理原始点云)







## 六、全景分割
### 6.1 3D
- [14-A Technical Survey and Evaluation of Traditional Point Cloud Clustering
Methods for LiDAR Panoptic Segmentation](https://blog.csdn.net/peng_258/article/details/132379011?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132379011%22%2C%22source%22%3A%22peng_258%22%7D)
> 语义分割 + 聚类算法 = 全景分割；将点云中对象分割成一个个物体



## 七、数据集
- [15-Toronto-3D: A Large-scale Mobile LiDAR Dataset for Semantic Segmentation ofUrban Roadways](https://blog.csdn.net/peng_258/article/details/132383232?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132383232%22%2C%22source%22%3A%22peng_258%22%7D)
> Toronto-3D 是一个带颜色信息城市道路语义分割的大规模的LiDAR数据集，该数据集的提出获得 2020 CVPR


## 八、目标检测
### 8.1 2D目标检测
- [16-SSD: Single Shot MultiBox Detector](https://blog.csdn.net/peng_258/article/details/132389509?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132389509%22%2C%22source%22%3A%22peng_258%22%7D)
> 提出使用单一深度神经网络来进行2D图像目标检测的方法 SSD


## 九、网络
- [19-Equivariant Multi-View Networks](https://blog.csdn.net/peng_258/article/details/132591021?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132591021%22%2C%22source%22%3A%22peng_258%22%7D)
> 在计算机视觉中，模型在不同视角下对数据（例如，点云、图像等）对数据的变化具有一定的响应性。为了使模型能够更好地适应这种变化，不是仅仅对某个特定视角的数据进行训练，研究人员提出了等变多视角网络的概念。





