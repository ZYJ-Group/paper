# 论文阅读训练 共三篇（大方向/篇数）
# Progress in small object detection for remote sensing images（标题）
- 袁翔 1，程塨 1（作者）
- Journal of Image and Graphics（刊物）
- 链接：[paper](1-Literature/遥感影像小目标检测研究进展_袁翔.pdf)
- 阅读时间：2023-07-29

### 标题、摘要、关键词
- 标题：遥感影像小目标检测研究进展
- 摘要：独特的拍摄视角和多变的成像高度使得遥感影像中包含大量尺寸极其有限的目标，如何准确有效地检测这 些小目标对于构建智能的遥感图像解译系统至关重要。本文聚焦于遥感场景，对基于深度学习的小目标检测进行全 面调研。首先，根据小目标的内在特质梳理了遥感影像小目标检测的 3 个主要挑战，包括特征表示瓶颈、前背景混淆以 及回归分支敏感。其次，通过深入调研相关文献，全面回顾了基于深度学习的遥感影像小目标检测算法。选取 3 种代 表性的遥感影像小目标检测任务，即光学遥感图像小目标检测、SAR 图像小目标检测和红外图像小目标检测，系统性 总结了 3 个领域内的代表性方法，并根据每种算法使用的技术思路进行分类阐述。再次，总结了遥感影像小目标检测 常用的公开数据集，包括光学遥感图像、SAR 图像及红外图像 3 种数据类型，借助于 3 种领域的代表性数据集 SODA-A （small object detection datasets）、AIR-SARShip 和 NUAA-SIRST（Nanjing University of Aeronautics and Astronautics， single-frame infrared small target），进一步对主流的遥感影像目标检测算法在面对小目标时的性能表现进行横向对比及 深入评估。最后，对遥感影像小目标检测的应用现状进行总结，并展望了遥感场景下小目标检测的发展趋势。
- 关键词：小目标检测（SOD）；深度学习；光学遥感图像；SAR 图像；红外图像；公开数据集


### 研究背景
- 大背景：遥感影像目标检测旨在设计相关算法获取遥感 图像中有价值目标的类别和位置信息，是迈向遥感 场景智能理解、构建遥感影像智能解译系统以及开 展遥感影像分析业务化应用的重要途径（孙显 等， 2022）。遥感图像具有幅面大、场景多样和成像高度 多 变 等 特 点 ，因 而 包 含 大 量 尺 寸 极 其 有 限 的 目 标 。 例如在同一幅机场场景光学遥感图像中，飞机和车 辆往往同时出现，而由于尺寸层面的天然差异，车辆 目标往往仅占据几十个像素（Cheng 等，2022c）。合 成孔径雷达（synthetic aperture radar，SAR）的目标成 像与目标的散射特性有关，散射特性的强弱影响目 标的成像质量，例如飞机目标的机翼散射特性弱、机 身散射特征强，机翼区域的成像较为模糊，这使得目 标在 SAR 图像中相对偏小。此外，特殊的成像机理 使目标容易受到杂波等噪声的干扰，导致目标边缘 模糊，使得本身尺寸较小的车辆、船舶等观测目标成 像区域更加受限（徐丰 等，2020）。红外探测系统 中，目标与探测器之间距离较远，因而成像目标面积 很小，往往呈现点特征（李俊宏 等，2020）。这些尺寸有限的目标给遥感影像智能感知系统带来了巨大 挑战，也在一定程度上制约着遥感大数据在国防体 系建设、灾害预警评估和农林资源监测等领域的实 际应用。
- 小背景：与通用目标检测的蓬勃发展相比，小目标检测 近年来发展缓慢，遥感图像领域亦是如此。作为通 用目标检测的一个子任务，现有的小目标检测框架 往往以通用目标检测任务中表现出色的模型为基 础，添加针对性的设计（Cheng 等，2022c）。这些基 础模型一般由特征提取网络和检测网络构成，前者 通过深度卷积神经网络（deep convolution neural net⁃ work）获得图像的高维表征，并利用下采样操作减少 空间冗余；后者则在前者得到的深度特征上完成分 类和回归（Liu 等，2020；Ren 等，2017；Lin 等，2020； Tian 等，2022）。遗憾的是，这些深度学习加持下的 优秀检测范式在面对小目标时，性能往往捉襟见肘。 究其原因，一方面是小目标的内在特性导致模型很 难获得目标区域的良好特征表示。CNN 通过堆叠 卷积层和池化层获得图像的高维表征，前者通过共 享参数的卷积核获得区域表示，而遥感图像中的小 目标往往背景复杂，经过卷积层后，目标区域的特征 容易被背景或其他实例所干扰，丢失判别信息；后者 旨在减少空间冗余并滤除噪声响应，然而这一操作 却为小目标带来不可逆的信息损失（Noh 等，2015）。 无论是缺乏判别性的特征表示，还是目标区域的信 息损失，都会加剧后续分类和回归的任务难度。另 一方面，深度学习是数据驱动的，获得性能优异的检 测模型需要大量注释良好的数据用于训练。然而， 小目标往往边缘模糊且视觉结构强依赖于图像质 量，很难准确获得其轮廓信息，因而标注误差较大，在 一定程度上误导网络训练。此外，现有数据集往往包含各种尺度的目标，小目标仅占其中一小部分，导 致模型为兼顾整体精度而牺牲小目标的检测效果。

### 研究内容
- 内容：本文选取 3 种代表 性的遥感影像小目标检测任务，即光学遥感图像小 目标检测、SAR 图像小目标检测和红外图像小目标 检测，以算法和数据集为研究对象，全面回顾基于深 度学习的遥感影像目标检测，并对应用现状和发展 趋势进行总结。

### 潜在研究点
- 基于已有研究和相关实验分析，展望遥 感影像小目标检测任务，潜在的几个未来发展方向 如下：1）适用于小目标相关下游任务的特征提取网 络。众所周知，特征表示的良好与否直接影响着后 续的任务精度。现有小目标检测算法均利用在通用 目标检测任务上大放异彩的主干网络如 ResNet 进 行特征提取，这些网络通过池化等下采样操作减少 空间维度冗余，却不可避免地造成小目标的信息丢 失，而这种丢失很难通过后续操作复原。因此，设计 有效的特征提取网络对于小目标相关任务至关重 要。2）面向遥感影像小目标检测的大规模数据集。 当前，无论是自然图像还是遥感图像小目标检测领 域，性能优异的算法几乎都依赖于深度学习。如前 所述，深度学习算法在训练时需要“喂入”大量的标 注数据，而遥感影像小目标检测领域尚缺乏拥有良 好标注的大规模数据集，尤其是对于 SAR 图像和红 外图像这两种常用于军事领域侦察的数据，这在很 大程度上制约着该领域的进一步发展。3）多模态遥 感数据协同的小目标检测算法。小目标算法性能羸 弱的根本原因在于可用信息极少，如果能够丰富信 息来源，就能在一定程度上缓解模型由于缺乏判别 性信息无法准确决策的问题。具体到遥感影像，随 着星座组网的进行和卫星多种载荷的搭配，不同模 式的卫星影像在时间密度和空间密度上显著提升， 通过不同模态数据之间的互补及协同应用，有效利 用各模态之间的信息进行优势互补，克服不同模态之间在时间和空间上的差异和信息不足短板，开发 基于多模态数据的遥感影像小目标检测算法是未来 发展的一个重要趋势。4）更合理灵活的性能评估标 准。目前的小目标检测评价体系大多沿用通用目标 检测领域的评估指标，并不适用于小目标检测任务。 因而设计更加灵活且合理的小目标检测评价标准， 不仅能够进一步优化模型训练，也能够准确反映各 算法的真实性能，引导领域的良性发展。

### 总结
- Conclusion by Thy: 本文主要介绍小目标检测。并将其归纳为了3个方面，即特征表示瓶颈、前背景混淆和回归分支敏感。

  ![image](https://github.com/ZYJ-Group/Tanghy/assets/94824386/0e6a8b3e-411c-4428-9ebf-69513011b079)

- 光学遥感图像小目标检测算法，根据算法采用技术的主 要特点，可概括为 5 类，即基于数据扩充的方法、基 于特征融合的方法、基于超分辨的方法、基于背景建 模的方法和基于优化训练策略的方法。

![image](https://github.com/ZYJ-Group/Tanghy/assets/94824386/e97ce976-f4d6-4a00-816f-fd287dae486d)

- 随着 SAR 成像技术的不断发展，高分辨率 SAR 图像的数据积累与日俱增，数据驱动的深度学习领 域涌现出一批代表性工作。这些方法往往以通用目 标检测算法为基础，结合小目标的表征特性与 SAR 成像机理优化网络设计，从而完成对 SAR 遥感图像 中的小目标的检测。根据其优化的机理与设计技术 的区别，可以概括为 5 类，即基于数据扩充增强的方 法、基于多尺度特征融合的方法、基于注意力特征感 知的方法、基于半监督学习的方法和基于雷达散射 机理的方法。整体的分类图如图所示。

![image](https://github.com/ZYJ-Group/Tanghy/assets/94824386/e9b12e56-f2ae-4e81-90b0-2248b1105db8)

- 随着红外成像技术的不断发展，结合深度学习 的红外图像小目标检测方法屡见不鲜。这些方法往 往以通用目标检测算法为基础，结合红外小目标的 特点优化网络设计，从而完成对红外图像中小目标 的检测。根据其优化手段与设计方法的区别，可以 概括为 4 类，即基于超分辨率的方法、基于背景噪声 抑制的方法、基于注意力机制的方法和基于多尺度 感知的方法。整体的分类图如图所示。

![image](https://github.com/ZYJ-Group/Tanghy/assets/94824386/1dcbdb3d-d979-43d7-8eb3-168dcb11801e)

- 文章后续还介绍了光学遥感、SAR、红外成像对应的数据集等数据。



