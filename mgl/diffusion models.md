# Diffusion Model 已更新文献数量4篇

## 4篇-Zewei Zhao  (Keywords:Diffusion Model for spatiotemporal prediction ) （篇数+作者信息+关键词）

- School of Information and Electronics and the Key Laboratory of Electronic and Information Technology in Satellite Navigation, Ministry of Education, Beijing Institute of Technology, Beijing, China（主要作者单位）

### 1Advancing Realistic Precipitation Nowcasting With a Spatiotemporal Transformer-Based Denoising Diffusion Model [ [IEEE Transactions on Geoscience and Remote Sensing](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=36),2024)[10.1109/TGRS.2024.3355755](https://doi.org/10.1109/TGRS.2024.3355755)（序号+文章名+发表刊物+年份+链接）

- 2023/4/25(阅读时间)

#### conclusion by MGL:

提出了一种新的生成去噪扩散建模范式。采用条件扩散技术，以过去的观测结果为条件，将高斯噪声逐渐映射到目标图像序列，以捕捉雷达图像序列中反映的真实降水时空分布。此外，为了实现快速采样速度，通过对大型反向扩散步骤的对抗映射，结合了快速扩散策略。最后，为了确保符合基于图像和气象的评估指标，并生成视觉上真实的雷达图像，

![1714053295804](imgages/1714053295804.png)

表二 基于图像的索引的性能指标。像素级图像质量指标包括 MSE、PSNR 和 SSIM，其中 MSE 值越低，PSNR 和 SSIM 值越高表示图像质量越好。感知指标包括 LPIPS、FID 和 RALSD，较低的值反映出更好的感知质量。

![1714052802840](imgages/1714052802840.png)

关于实验结果非常有意思，本文提出的方法在像素级评估指标 MSE、PSNR 和 LPIPS 方面表现都不是最佳，但与 ConvLSTM、MotionRNN 和 SimVP 相比，在 FID 和 RALSD 方面有所改善。基于cGAN的方法和基于扩散模型的方法在像素级图像评估指标上都没有表现出明显的优势。然而，他们在获得高感知分数方面表现出色。在短期预测系统的评估中，强调感知评分的重要性是很重要的。由于预报结果是为预报员和公众准备的，因此它们应该在视觉上清晰，并与人类的感知保持一致。值得注意的是，我们的方法在上述所有指标上都优于 GAN 方法。

#### conclusion by MGL:

时空预测目前的方法要么基于确定性模型（LSTM,RNN等），要么基于生成模型（GAN,扩散）。确定性模型将依靠距离函数（如 L2 范数损失）进行训练。在改善预测图像质量评价指标的同时，不可避免地会产生模糊的预测，没有参考价值。相比之下，生成模型旨在捕获真实的降水分布(自身运动)，并通过在这些分布中采样来生成预测图像。

在实验阶段,为了评估模型性能，baseline采用包括ConvLSTM [19] 、MotionRNN [21] 、SimVP [58] 、SVG [59] 和基于条件GAN [60] 的方法。为接下来的自己的baseline提供参考。另外，很多文章包括本文都把原始扩散模型原理及公式放在第二章部分，更好的比较，条件GAN [60] 的方法对比实验必须加，因为肯定可以碾压它。
## 3篇-Jun Yue (Keywords:Diffusion Model;Image fusion;deep generative model ) （篇数+作者信息+关键词）

- School of Automation, Central South University, Changsha, China（主要作者单位）

### 1 Dif-Fusion: Toward High Color Fidelity in Infrared and Visible Image Fusion With Diffusion Models ( [IEEE Transactions on Image Processing](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=83) 2023) https://doi.org/10.1109/TIP.2023.3322046   （序号+文章名+发表刊物+年份+链接）

- 2024/3/8(阅读时间)

#### conclusion by MGL:基于扩散模型的红外-可见光图像融合方法，实现多通道互补信息提取，有效保持色彩和视觉质量。一方面，利用正反向扩散过程构建了潜在空间中多通道输入数据的分布。通过训练逆向过程中的去噪网络来预测前向过程中增加的高斯噪声，构建多通道数据的分布。直接生成彩色融合图像，并同时实现颜色、梯度和强度的保真度。

![1709971639007](images/1709971639007.png)

 这篇文章也是基于扩散模型，论文写作的大致流程非常值得借鉴，比如本文在方法里叙述原始扩散模型分为三个部分介绍 正向扩散过程过程，反向扩散过程以及损失函数，之后在第二章叙述的是相关工作分为两部分A. 红外和可见光图像融合；包括传统方法和基于深度学习的方法；B. 扩散模型；B部分可以直接借鉴写法；A部分我们可以叙述预测；同时也包括传统方法和基于深度学习的方法；以及后面的实验部分

这篇文章使用的三个公共数据集进行定量和定性分析，以评估所提出的框架。此外，与六个最先进的模型进行了比较，并且 有两种是基于 CNN 架构的融合方法，而 另外四种是基于生成模型及其变体的；代码公开；比较有信服力。红外-可见光图像融合这种方法是不是也可以拓展到 ISAR和光学图像的融合；若有必要，可再仔细读。


## 2篇-Jiaming Song （DENOISING DIFFUSION IMPLICIT MODELS）[paper](images/ddim.pdf)  
- Stanford University
### DENOISING DIFFUSION IMPLICIT MODELS (ICLR 2021)
- 2023.10.23
### Situation
生成模型现在主要分为两类，分别是GAN和Diffusion Model，但是GAN存在一个很棘手的问题就是训练不稳定，这也是Diffusion Model相比之下的优势。DDPM是基于Markovian扩散过程的模型，虽然在生成模型上取得了不错的效果，但是同时也存在一个大缺点，就是由于在重建生成阶段是需要一步步进行，步数通常为2000，导致推理时间非常长，需要多次迭代才能产生高质量的生成样本，

![](images/912.png)

####  conclusion by MGL: 相较于DDPM来说，DDIM更具更加确定性的结果，并且可以减少一定的计算时间。DDPM是可以通过改变一定的参数比如论文中的是可以互相转化的，其实也提供了另外一种模型的思路，比如也可以只用DDIM中论文的一部分来减少DDPM模型的计算时间，或者直接应用DDIM在参数上改变，看看能否对超分辨或者图像降噪等问题有新的实验发现。注意：DDIM只是在重建阶段使用，Unet训练的参数和DDPM是一样的，也就是说是通过DDPM训练参数得到的Unet模型应用到DDIM上的，这点是不变的









## 1篇-Jonathan Ho (Denoising Diffusion Probabilistic Models)[paper](images/ddpm.pdf)
-UC Berkeley 

### 34th Conference on Neural Information Processing Systems (NeurIPS 2020), Vancouver, Canada
-2023/10/15(阅读时间)

### Situation：
各种深度生成模型最近展示了各种数据模式的高质量样本。生成对抗网络（GAN）、自回归模型、流和变分自编码器（VAE）已经合成了引人注目的图像和音频样本，并且在基于能量的建模和分数匹配方面取得了显着进展，产生了与GAN相当的图像[。

### Task
使用扩散概率模型呈现高质量的图像合成结果,扩散概率模型是一类受非平衡热力学考虑启发的潜在变量模型

#### Action 

生成扩散模型DDPM如下图所示分为前向、逆向两个过程，它首先通过不断往原始清晰数据中添加噪声使其变成标准高斯噪声（前向过程），而后期望从标准高斯噪声中还原原始数据（逆向过程）。若能实现，那我们便可从已知的标准高斯分布中采样一个噪声数据，而后利用DDPM模型生成符合原始数据分布的新数据啦。下面将分别从前向过程和逆向过程两个角度解析DDPM算法。

![10.173z](images/10.173.png)  


在DDPM的前向过程中，通过下式往原始数据中逐步添加高斯噪声**（添加噪声的过程被假设为服从马尔可夫过程）**， T步过后（ T 足够大，在原始论文中作者取值是1000），数据就将变成纯高斯噪声 Z~N(0，I)、

   假设，
   ![](images/10174.png)
后一时刻分布是有前一时刻加噪得到的

![10176z](images/10176.png)

![10177z](images/10177.png)

![10175z](images/10175.png)

利用马尔科夫过程特性以及高斯分布的叠加性得到

推导过程如下：


![10175z](images/10178.png)


反向过程： 

​                                  前项过程提供标签 ，反向过程用这个标签去预测 噪声分布 Zt 

![](images/10.172.png)

算法一，训练过程，

![10.17z](images/10.17.png)

![10.171z](images/10.171.png)

### Result

使用扩散模型展示了高质量的图像样本,我们的最佳结果是通过根据扩散概率模型与Langevin动力学的去噪分数匹配之间的新联系设计的加权变分边界进行训练而获得的，并且我们的模型自然地承认渐进式有损解压缩方案，可以解释为自回归解码的推广。在无条件CIFAR10数据集上，我们获得了 9.46 的 Inception 分数和 3.17 的最先进的 FID 分数。在256x256 LSUN上，我们获得了类似于ProgressiveGAN的样品质量。
