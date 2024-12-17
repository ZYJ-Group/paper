## 1.**An improved algorithm for PRI Modulation Recognition**

Yanchao Liu；Qunying Zhang

IEEE International Conference on Signal Processing, Communications and Computing (ICSPCC)    2017

https://ieeexplore.ieee.org/document/8242587

**主要内容：**

这篇文章是在信号分选（去交织）的步骤之后展开工作的，写了如何正确的提取不同PRI调制类型的特征。

文章通过对一阶脉冲间隔和二阶脉冲间隔进行分析，通过sgn函数来实现了对Jittered，Sliding，Dwell and Switch，Wobulated，进行分离处理，再对得到信号的**局部平稳性、单调方向性和对称性**作为特征，然后设计一个简单的网络进行识别。

**总 结：**

可以学习通过预处理的方式，来使得其特征更为突出，然后在做后面的处理工作。

## **2.SLNet: A Spectrogram Learning Neural Network for** **Deep Wireless Sensing**

Zheng Yang , Yi Zhang , Kun Qian , Chenshu Wu

[SLNet: A Spectrogram Learning Neural Network for Deep Wireless Sensing | USENIX](https://www.usenix.org/conference/nsdi23/presentation/yang-zheng)

[[2206.09532\] Hands-on Wireless Sensing with Wi-Fi: A Tutorial](https://arxiv.org/abs/2206.09532)

主要内容：

SLNet 采用神经网络生成超分辨率频谱图，克服了时频不确定性的限制。然后，它利用一种新的极化卷积网络来调制频谱图的相位，以学习局部和全局特征。然后在手势识别、人体识别、跌倒检测和呼吸估计四个方面的实验中，实现了以最小的计算消耗，获得拥有最好的性能。

![{B795FC00-19EE-4EED-AC4F-D0ACB42B1742}](images/%7BB795FC00-19EE-4EED-AC4F-D0ACB42B1742%7D.png)

![{0CB11767-4E2A-4547-BBFC-C7B6044953CF}](images/%7B0CB11767-4E2A-4547-BBFC-C7B6044953CF%7D.png)

![{FC23838E-A21E-49CE-A53C-EE90079DE5BD}](images/%7BFC23838E-A21E-49CE-A53C-EE90079DE5BD%7D.png)

