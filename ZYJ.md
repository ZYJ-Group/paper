
# Attitude-Estimation-of-satellites （大方向）

## 1-Dan Shen (Keywords: satellite behavior discovery) （作者信息+关键词）
-Chief Scientist of Intelligent Fusion, Germantown, MD, USA
### Publications
   - Three-dimensional convolutional neural network (3D-CNN) for satellite behavior discovery (Proc. SPIE 11755, Sensors and Systems for
Space Applications XIV) [paper](https://drive.google.com/file/d/1GsvANy0GqKeGugN_fYaX9QIjB-10Q-Lk/view) 
     - 2022/11/19 (阅读时间)
     - comments by ZYJ: 根据地面测量的距离、方位、俯仰、RCS序列去对目标行为进行分类，使用Adaptive Markov Inference Game Optimization (AMIGO)仿真软件构造数据集，并搭建一个3D CNN网络进行行为识别，对比实验是之前的2D CNN精度提升了（ 95.3% VS  92.1%）。 文章比较水，大部分篇幅在科普网络结构，行为标签没说怎么来的，可以是:增加orbital energy，减少orbital energy，以及0机动（zero-maneuver）。
     - conclusion by ZYJ:文章扫两眼就行了，后面可以找找之前有没有标签定义的先前工作。
     - <img width="694" alt="image" src="https://user-images.githubusercontent.com/19592290/201851463-8ae227d4-e38a-4be8-a4bf-73c6c30e91b6.png">

   - Cooperative Space Object Tracking Using Space-Based Optical Sensors via Consensus-Based Filters (IEEE TRANSACTIONS ON AEROSPACE AND ELECTRONIC SYSTEMS VOL. 52, NO. 4, 2016) [paper](https://www.researchgate.net/profile/Erik-Blasch/publication/310467221_Cooperative_space_object_tracking_using_space-based_optical_sensors_via_consensus-based_filters/links/5f33ed19458515b72918a326/Cooperative-space-object-tracking-using-space-based-optical-sensors-via-consensus-based-filters.pdf) 
     - 2022/11/20 (阅读时间)
     - comments by ZYJ: 基于天基卫星的角度测量去辅助更新目标在轨的位置，主要对比了几类滤波算法，如the information-weighted consensus filter (ICF)、 the Kalman consensus filter (KCF)。实验主要搭建了三个观测场景：1、Cooperative Tracking of a GEO Object；2、 Cooperative Tracking of an Object with an EO； 3、 Cooperative Tracking of Two Close Objects。结论是多天基联合跟踪算法比单基的好，基于共识的分布式估计（the consensus-based distributed estimation）可以接近集中式估计（the centralized estimation algorithms）的性能。
     - conclusion by ZYJ:主要集中于跟踪算法的改进，跟目前研究目的不大相关，有需要状态预测再仔细读。
     - <img width="400" alt="image" src="https://user-images.githubusercontent.com/19592290/202881206-699045e8-acdb-4453-8efd-a167d515b2dd.png">  <img width="400" alt="image" src="https://user-images.githubusercontent.com/19592290/202881216-e4be7dff-c060-4993-83e6-dda226990de5.png">  <img width="400" alt="image" src="https://user-images.githubusercontent.com/19592290/202881231-54245e23-b41a-4ce5-9010-300a039db1b8.png">
     - <img width="500" alt="image" src="https://user-images.githubusercontent.com/19592290/202881030-3931d064-73ff-49c3-96ad-ac3f30b3bb09.png">
    

