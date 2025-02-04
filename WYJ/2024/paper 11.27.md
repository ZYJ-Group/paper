
# SuperPiont

SuperPiont是一种自监督网络框架，能够同时提取特征点的位置以及描述子

## 整体步骤

**三个部分**
![image](https://github.com/ZYJ-Group/paper/blob/main/WYJ/img/11.27(1).jpg)
1. 特征点预训练
   创建合成数据集 Synthetic Shapes， 利用合成数据集搭建SuperPoint。训练结果在合成数据集 Synthetic Shapes上，显著优于传统的兴趣点检测器,这里训练出的检测器叫MagicPoint。
2. 自监督标签
   用 1 中训练好的检测器MagicPoint得到数据集的特征点。由此 self-supervised dataset 训练而产生的检测结果具有更强的可重复性。
    
    
3. 联合训练


## 框架及原理

![image](https://github.com/ZYJ-Group/paper/blob/main/WYJ/img/11.27(2).png)
1.Shared Encoder 共享编码网络
输入（H,W）的图像，经过4次block块（每一个块包括2个卷积层和最大池化层，最后一次没有池化层），池化层选用的步长step为2，每一次 tensor 尺寸就缩小一倍。最终输出的就是（Hc,Wc,128）的 tensor。其中Hc=H/8，Wc=W/8。

2.Interest Point Decoder 特征点解码网络

经过两层卷积获得（Hc，Wc，65）的tensor。其中65代表原尺寸8x8的范围的，与之一一对应。（64+1，最后那1位进行舍去dustbin）。对每一个通道（65位）进行softmax过程中会舍去

3.Descriptor Decoder 特征点描述网络

使用encoder层的输出（Hc,Wc,128）。经过卷积解码器得到（Hc,Wc,256），双线性插值扩大尺寸（H,W,256），最后对每一个像素的描述子进行L2归一化。

4.损失函数
损失函数设计分为三部分：Lp：特征点损失；Lp'：右图特征点损失；Ld：特征描述损失

最终损失是两个中间损失的总和：
![image](https://github.com/ZYJ-Group/paper/blob/main/WYJ/img/f1.png)

其中Lp：特征点损失：
![image](https://github.com/ZYJ-Group/paper/blob/main/WYJ/img/f2.png)
![image](https://github.com/ZYJ-Group/paper/blob/main/WYJ/img/f3.png)

Ld：特征描述损失

判定p与p'的距离:
![image](https://github.com/ZYJ-Group/paper/blob/main/WYJ/img/f4.png)

![image](https://github.com/ZYJ-Group/paper/blob/main/WYJ/img/f5.png)
![image](https://github.com/ZYJ-Group/paper/blob/main/WYJ/img/f6.png)

d与d'越相似，loss越小
