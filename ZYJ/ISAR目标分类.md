# ISAR Image Classification 已更新文献数量 2 篇
## 1篇- Xu Gang (Keywords: ISAR Image Classification) 
-State Key Laboratory of Millimeter Waves, Southeast University
### CLISAR-Net: A Deformation-Robust ISAR Image Classification Network Using Contrastive Learning. (Remote Sensing, 2022.)[paper](https://www.mdpi.com/2072-4292/15/1/33/pdf)
   - 2023/01/03 (阅读时间)
#### comments by ZYJ: 基于对比学习提取运动引起的图像特征形变（deformation），然后实现不同空间目标的分类。第一阶段无监督训练，通过两个编码器根据InfoNCE (Noise Contrastive Estimation) loss[paper](https://arxiv.org/pdf/1807.03748.pdf)实现聚焦图像与非聚焦图像间的差异学习，然后第二个阶段使用少部分样本进行带标签的分类训练。
   - <img width="500" alt="image" src="https://user-images.githubusercontent.com/19592290/210315110-daf75bfe-b087-4d7d-90de-b817edad14fa.png"> 
   - <img width="500" alt="image" src="https://user-images.githubusercontent.com/19592290/210315184-51dab657-5107-49d3-9d18-de951f62fa4d.png"> 
####    中间对比学习（Contrastive Learning）有一些点还可以，整体任务比较简单。实验基于HFSS仿真了4个目标，每个实验数据集规模在2000+2000，用了一张3090。
   - <img width="500" alt="image" src="https://user-images.githubusercontent.com/19592290/210314657-2aba5d41-848a-4113-b7c0-a25c5d1cee9a.png"> 
   - <img width="500" alt="image" src="https://user-images.githubusercontent.com/19592290/210315529-27be8d10-e5af-44a6-af56-0b4aef312e99.png"> 
#### conclusion by ZYJ: 可以当作入门文章，网络工作量应该不大，关键在于HFSS仿真，对比学习需要搞清楚无监督中样本对的差异InfoNCE怎么定义。

## 1篇- Bai Xueru (Keywords: ISAR Image Classification) 
- Xidian University
### SAISAR-Net: A Robust Sequential Adjustment ISAR Image Classification Network. (IEEE TRANSACTIONS ON GEOSCIENCE AND REMOTE SENSING, 2022.)[paper](https://ieeexplore.ieee.org/abstract/document/9552492)
   - 2023/01/04 (阅读时间)
#### comments by ZYJ: 基于注意力提升（Attention Augmented）的Bi-LSTM对形变（deformation）ISAR图像序列进行有监督的训练分类。
   - <img width="600" alt="image" src="https://user-images.githubusercontent.com/19592290/210518328-0423927e-6917-4a84-90f6-51a1afc75646.png"> <img width="300" alt="image" src="https://user-images.githubusercontent.com/19592290/210518493-c100c103-27b5-4a7e-833c-c7310bcede41.png"> 
####   实验基于电磁仿真了HV极化目标成像结果，每个实验数据集规模在2000，单帧大小128X128，序列长度3-15，用了一张2080 Ti，实验比较充分。
   - <img width="500" alt="image" src="https://user-images.githubusercontent.com/19592290/210520129-6365ba1f-d465-462c-acee-09938af6fb81.png"> <img width="500" alt="image" src="https://user-images.githubusercontent.com/19592290/210520413-b2b22f34-417e-4e12-9b3a-328ee517bbe1.png"> 
#### conclusion by ZYJ: 可以当作网络方向参考文章，写得可以。
