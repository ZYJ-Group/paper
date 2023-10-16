# Diffusion Models 

## 1 Jonathan Ho (Denoising Diffusion Probabilistic Models)[paper](images/ddpm.pdf)
-UC Berkeley 

### 34th Conference on Neural Information Processing Systems (NeurIPS 2020), Vancouver, Canada
-2023/10/15(阅读时间)

### Situation：
各种深度生成模型最近展示了各种数据模式的高质量样本。生成对抗网络（GAN）、自回归模型、流和变分自编码器（VAE）已经合成了引人注目的图像和音频样本，并且在基于能量的建模和分数匹配方面取得了显着进展，产生了与GAN相当的图像[。

### Task
使用扩散概率模型呈现高质量的图像合成结果,扩散概率模型是一类受非平衡热力学考虑启发的潜在变量模型

#### Action 

生成扩散模型DDPM如下图所示分为前向、逆向两个过程，它首先通过不断往原始清晰数据中添加噪声使其变成标准高斯噪声（前向过程），而后期望从标准高斯噪声中还原原始数据（逆向过程）。若能实现，那我们便可从已知的标准高斯分布中采样一个噪声数据，而后利用DDPM模型生成符合原始数据分布的新数据啦。下面将分别从前向过程和逆向过程两个角度解析DDPM算法。

![10.173](F:\新桌面\ZUT\reading\images\10.173.png)



在DDPM的前向过程中，通过下式往原始数据中逐步添加高斯噪声**（添加噪声的过程被假设为服从马尔可夫过程）**， T步过后（ T 足够大，在原始论文中作者取值是1000），数据就将变成纯高斯噪声 Z~N(0，I)

 

   假设，

![10174](F:\新桌面\ZUT\reading\images\10174.png)

后一时刻分布是有前一时刻加噪得到的



![10176](F:\新桌面\ZUT\reading\images\10176.png)

![10177](F:\新桌面\ZUT\reading\images\10177.png)

![10175](F:\新桌面\ZUT\reading\images\10175.png)

利用马尔科夫过程特性以及高斯分布的叠加性得到

推导过程如下：

![83ec62168fe404dd8c82e55d59b5fc2](D:\WeChat Files\wxid_1quzcu7y2me722\FileStorage\Temp\83ec62168fe404dd8c82e55d59b5fc2.png)



反向过程： 

​                                  前项过程提供标签 ，反向过程用这个标签去预测 噪声分布 Zt ![67edc0d484f139fb075b3299f1a2add](D:\WeChat Files\wxid_1quzcu7y2me722\FileStorage\Temp\67edc0d484f139fb075b3299f1a2add.png)



![18bdc1371ecf4b4f7adfdba3179dcbd](D:\WeChat Files\wxid_1quzcu7y2me722\FileStorage\Temp\18bdc1371ecf4b4f7adfdba3179dcbd.png)                                                        ![4ca6f856d1fe7ab1505130a2cfc0b44](D:\WeChat Files\wxid_1quzcu7y2me722\FileStorage\Temp\4ca6f856d1fe7ab1505130a2cfc0b44.png)

![10.172](F:\新桌面\ZUT\reading\images\10.172.png)

算法一，训练过程，

：![10.17](F:\新桌面\ZUT\reading\images\10.17.png)

![10.171](F:\新桌面\ZUT\reading\images\10.171.png)

### Result

使用扩散模型展示了高质量的图像样本,我们的最佳结果是通过根据扩散概率模型与Langevin动力学的去噪分数匹配之间的新联系设计的加权变分边界进行训练而获得的，并且我们的模型自然地承认渐进式有损解压缩方案，可以解释为自回归解码的推广。在无条件CIFAR10数据集上，我们获得了 9.46 的 Inception 分数和 3.17 的最先进的 FID 分数。在256x256 LSUN上，我们获得了类似于ProgressiveGAN的样品质量。