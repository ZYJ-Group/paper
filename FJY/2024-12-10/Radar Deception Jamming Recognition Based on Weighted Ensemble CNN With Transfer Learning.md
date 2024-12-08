## **Radar Deception Jamming Recognition Based on Weighted Ensemble CNN With Transfer Learning**

#### **Keywords :Convolutional neural network (CNN), deception jamming recognition, ensemble learning, small sample, transfer learning.**

IEEE TRANSACTIONS ON GEOSCIENCE AND REMOTE SENSING, VOL. 60, 2022

https://ieeexplore.ieee.org/abstract/document/9622244

**解决问题：**

小样本情况下，因为其训练样本过少，难以充分覆盖数据分布，易致模型过拟合，所以会导致深度学习算法的准确性不太好。

**其创新点：**

1. 通过STFT获得时频分布，并将其实部，虚部，幅值和相位作为数据集。
2. 设计了一个新的WECNN-L，其结合了迁移学习和加权集成算法。

#### **内容**

针对雷达抗干扰中欺骗干扰识别难题，鉴于小样本下深度学习算法局限，提出WECNN-TL算法。加上*Ensemble Learning*和*Transfer Learning*。

创新地将时频域特征构建多数据集，并提取其实部， 虚部，幅值和相的信息，作为子数据集，再将这些子数据集排列组合，再通过设计的加权投票与迁移学习机制提升模型性能。

该算法在小样本的情况相比于其他方法性能较好。

![{1E3857DC-E7F4-462F-ACCB-966E472C4C0C}](C:\Users\Administrator\AppData\Local\Packages\MicrosoftWindows.Client.CBS_cw5n1h2txyewy\TempState\ScreenClip\{1E3857DC-E7F4-462F-ACCB-966E472C4C0C}.png)

![{0978C188-7614-4DEF-8D02-2BE7F07B9CA5}](C:\Users\Administrator\AppData\Local\Packages\MicrosoftWindows.Client.CBS_cw5n1h2txyewy\TempState\ScreenClip\{0978C188-7614-4DEF-8D02-2BE7F07B9CA5}.png)

**其权重计算公式：**

![{91DEECFD-79B0-4A19-9FD3-1D14BADE3F4E}](C:\Users\Administrator\AppData\Local\Packages\MicrosoftWindows.Client.CBS_cw5n1h2txyewy\TempState\ScreenClip\{91DEECFD-79B0-4A19-9FD3-1D14BADE3F4E}.png)

![{987BD2C5-B897-4314-A986-5E9325332C13}](C:\Users\Administrator\AppData\Local\Packages\MicrosoftWindows.Client.CBS_cw5n1h2txyewy\TempState\ScreenClip\{987BD2C5-B897-4314-A986-5E9325332C13}.png)



**实验结果:**

与多种基本的方法对比，也与固定权重ECNN，不加迁移学习WECNN的方法做对比，实验结果证明其在小样本的情况下各个性能指标都有提示，且是否具有固定权重的影响比是否加入迁移学习的影响更大，后者主要体现在其运行时间的差异。



感觉整个流程框架可以借鉴一下，可以试一下替换文章中的卷积网络。