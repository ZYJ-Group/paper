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
> 基于投影的方法
---
- [12-RandLA-Net: Efﬁcient Semantic Segmentation of Large-Scale Point Clouds](https://blog.csdn.net/peng_258/article/details/132085815?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132085815%22%2C%22source%22%3A%22peng_258%22%7D)
> 基于点的方法(直接处理原始点云)

### 5.2 2D





## 六、3D点云全景分割
- [14-A Technical Survey and Evaluation of Traditional Point Cloud Clustering
Methods for LiDAR Panoptic Segmentation](https://blog.csdn.net/peng_258/article/details/132379011?csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22132379011%22%2C%22source%22%3A%22peng_258%22%7D)
> 语义分割 + 聚类算法 = 全景分割；将点云中对象分割成一个个物体







