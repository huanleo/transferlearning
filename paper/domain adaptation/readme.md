### Domain adaptation介绍及代表性文章梳理

Domain adaptation，DA，中文可翻译为域适配、域匹配、域适应，是迁移学习中的一类非常重要的问题，也是一个持续的研究热点。Domain adaptation可用于计算机视觉、物体识别、文本分类、声音识别等常见应用中。这个问题的基本定义是，假设源域和目标域的类别空间一样，特征空间也一样，但是数据的分布不一样，如何利用有标定的源域数据，来学习目标域数据的标定？

事实上，根据目标域中是否有少量的标定可用，可以将domain adaptation大致分为无监督（目标域中完全无label）和半监督（目标域中有少量label）两大类。我们这里偏重介绍无监督。

#### 形式化

给定：有标定的$\mathcal{D}_{S}=\{X_{S_i},Y_{S_i}\}^{n}_{i=1}$，以及无标定的$\mathcal{D}_{T}=\{X_{T_i},?\}^{m}_{i=1}$

求：$\mathcal{D}_{T}$的标定$Y_{T}$ （在实验环境中，$\mathcal{D}_{T}$是有标定的，仅用来测试算法精度）

条件：
- $X_{S},X_{T} \in \mathbf{R}^{p \times d}$，即源域和目标域的特征空间相同（都是$d$维）
- \{$Y_{S}\}=\{Y_{T}\}$，即源域和目标域的类别空间相同
- $P(X_S) \ne P(X_T)$，即源域和目标域的数据分布不同

#### 例子

比如说，同样都是一台电脑，在不同角度，不同光照，以及不同背景下拍照，图像的数据具有不同的分布，但是从根本上来说，都是一台电脑的图像。Domain adaptation要做的就是，如何根据这些不同分布的数据，很好地学习缺失的标定。

![Domain adaptation](https://raw.githubusercontent.com/jindongwang/transferlearning/master/png/domain%20_adaptation.png)

#### 代表方法与文章

Domain adaptation可以算是迁移学习领域最火的研究点了。因此，试图来解决此问题的方法层出不穷。从早期的基于实例的迁移、基于模型的迁移，到偏重数学变换的基于特征的迁移，再到如今的深度迁移，诞生了许多经典的DA方法。我们不打算面面俱到，也没有必要。在这里仅列出最经典的那些方法（何为最经典？引用量大且发表会议/刊物级别高），并在之后单独写文章深入介绍每个方法。时间有限，并且为了保证质量，不可能一次做完。

代表性的方法及文章：

- 迁移成分分析方法(Transfer component analysis, TCA)
	- [Domain adaptation via tranfer component analysis](https://github.com/jindongwang/transferlearning/blob/master/paper/domain%20adaptation/Domain%20Adaptation%20via%20Transfer%20Component%20Analysis_Sinno%20Jialin%20Pan%20et%20al_2011.pdf)
	- 发表在IEEE Trans. Neural Network期刊上（现改名为IEEE trans. Neural Network and Learning System），前作会议文章发在AAAI-09上
- 测地线流式核方法(Geodesic flow kernel, GFK)
	- [Geodesic flow kernel for unsupervised domain adaptation](https://github.com/jindongwang/transferlearning/blob/master/paper/domain%20adaptation/Geodesic%20flow%20kernel%20for%20unsupervised%20domain%20adaptation_Gong%20et%20al_2012.pdf)
	- 发表在CVPR-12上
- 领域不变性迁移核学习(Transfer Kernel Learning, TKL)
	- [Domain invariant transfer kernel learning](https://github.com/jindongwang/transferlearning/blob/master/paper/domain%20adaptation/Domain%20Invariant%20Transfer%20Kernel%20Learning_Long%20et%20al_2015.pdf)
	- 发表在IEEE Trans. Knowledge and Data Engineering期刊上
- TBD

接下来会继续添加方法，以及开始对每种方法的细致说明