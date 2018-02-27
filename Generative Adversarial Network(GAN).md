Generative Adversarial Network 生成对抗网络

unsupervised learning, implemented by a system of two [neural networks](https://en.wikipedia.org/wiki/Neural_network) contesting with each other in a [zero-sum game](https://en.wikipedia.org/wiki/Zero-sum_game) framework. They were introduced by [Ian Goodfellow](https://en.wikipedia.org/wiki/Ian_Goodfellow) *et al.* in 2014

生成对抗网络由一个[生成网络](https://zh.wikipedia.org/wiki/%E7%94%9F%E6%88%90%E6%A8%A1%E5%9E%8B)与一个[判别网络](https://zh.wikipedia.org/wiki/%E5%88%A4%E5%88%AB%E6%A8%A1%E5%9E%8B)组成。生成网络从潜在空间（latent space）中随机采样作为输入，其输出结果需要尽量模仿训练集中的真实样本。判别网络的输入则为真实样本或生成网络的输出，其目的是将生成网络的输出从真实样本中尽可能分辨出来。而生成网络则要尽可能地欺骗判别网络。两个网络相互对抗、不断调整参数，最终目的是使判别网络无法判断生成网络的输出结果是否真实。[[1\]](https://zh.wikipedia.org/wiki/%E7%94%9F%E6%88%90%E5%AF%B9%E6%8A%97%E7%BD%91%E7%BB%9C#cite_note-MyUser_Arxiv.org_April_7_2016c-1)[[2\]](https://zh.wikipedia.org/wiki/%E7%94%9F%E6%88%90%E5%AF%B9%E6%8A%97%E7%BD%91%E7%BB%9C#cite_note-OpenAI_com-2)

Typically, the generative network learns to map from a [latent space](https://en.wikipedia.org/wiki/Latent_variable) to a particular data distribution of interest, while the discriminative network discriminates between instances from the true data distribution and candidates produced by the generator. The generative network's training objective is to increase the error rate of the discriminative network (i.e., "fool" the discriminator network by producing novel synthesized instances that appear to have come from the true data distribution).[[3\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-MyUser_Arxiv.org_April_7_2016c-3)[7]



In practice, a known dataset serves as the initial training data for the discriminator. Training the discriminator involves presenting it with samples from the dataset, until it reaches some level of accuracy. Typically the generator is seeded with a randomized input that is sampled from a predefined latent space[[4\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-DAGUI-4) (e.g. a [multivariate normal distribution](https://en.wikipedia.org/wiki/Multivariate_normal_distribution)). Thereafter, samples synthesized by the generator are evaluated by the discriminator. [Backpropagation](https://en.wikipedia.org/wiki/Backpropagation) is applied in both networks [[5\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-DABUI-5) so that the generator produces better images, while the discriminator becomes more skilled at flagging synthetic images.[[8\]](https://en.wikipedia.org/wiki/Generative_adversarial_network#cite_note-OpenAI_com-8) The generator is typically a deconvolutional neural network, and the discriminator is a [convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network).



生成对抗网络常用于生成以假乱真的图片。[[3\]](https://zh.wikipedia.org/wiki/%E7%94%9F%E6%88%90%E5%AF%B9%E6%8A%97%E7%BD%91%E7%BB%9C#cite_note-ITT_GANs-3)此外，该方法还被用于生成视频[[4\]](https://zh.wikipedia.org/wiki/%E7%94%9F%E6%88%90%E5%AF%B9%E6%8A%97%E7%BD%91%E7%BB%9C#cite_note-4)、三维物体模型[[5\]](https://zh.wikipedia.org/wiki/%E7%94%9F%E6%88%90%E5%AF%B9%E6%8A%97%E7%BD%91%E7%BB%9C#cite_note-5)等。

**GAN Schematics**

![GAN schematics](https://pic3.zhimg.com/80/v2-61e1b1a6d1feb23a7d3c52966d11be08_hd.jpg)



Ref:

[Generative Adversarial Networks](https://arxiv.org/find/stat/1/au:+Bengio_Y/0/1/0/all/0/1)

[Advantage of GAN](https://zhuanlan.zhihu.com/p/25439613?refer=ml-simple)

[Ian GoodFellow](https://www.quora.com/What-is-the-advantage-of-generative-adversarial-networks-compared-with-other-generative-models)  

相比其他所有模型,

- 从实际结果来看,GAN看起来能产生更好的生成样本
- GAN框架可以训练任何生成网络(理论上，然而在实践中,很难使用增强学习去训练有离散输出的生成器),大多数其他架构需要生成器有一些特定的函数形式,就像输出层必须是高斯化的. 另外所有其他框架需要生成器整个都是非零权值(put non-zero mass everywhere),然而,GANs可以学习到一个只在靠近真实数据的地方(神经网络层)产生样本点的模型( GANs can learn models that generate points only on a thin manifold that goes near the data.)
- 没有必要遵循任何种类的因子分解去设计模型,所有的生成器和鉴别器都可以正常工作
- 相比PixelRNN, GAN生成采样的运行时间更短,GANs一次产生一个样本,然而PixelRNNs需要一个像素一个像素的去产生样本;
- 相比VAE, GANs没有变分下界,如果鉴别器训练良好,那么生成器可以完美的学习到训练样本的分布.换句话说,GANs是渐进一致的,但是VAE是有偏差的
- 相比深度玻尔兹曼机, GANs没有变分下界,也没有棘手的配分函数,样本是一次生成的,而不是重复的应用马尔科夫链来生成的
- 相比GSNs, GANs产生的样本是一次生成的,而不是重复的应用马尔科夫链来生成的;
- 相比NICE和Real NVE,GANs没有对潜在变量(生成器的输入值)的大小进行限制; 

[Ian GoodFellow ](https://www.quora.com/What-are-the-pros-and-cons-of-using-generative-adversarial-networks-a-type-of-neural-network-Could-they-be-applied-to-things-like-audio-waveform-via-RNN-Why-or-why-not)

**优势** 

- GANs是一种以半监督方式训练分类器的方法,可以参考我们的[NIPS paper](http://link.zhihu.com/?target=https%3A//arxiv.org/abs/1606.03498)和[相应代码](http://link.zhihu.com/?target=https%3A//github.com/openai/improved-gan).在你没有很多带标签的训练集的时候,你可以不做任何修改的直接使用我们的代码,通常这是因为你没有太多标记样本.我最近也成功的使用这份代码与谷歌大脑部门在[深度学习的隐私方面](http://link.zhihu.com/?target=https%3A//qz.com/814934/ai-can-learn-from-data-without-ever-having-access-to-it/)合写了[一篇论文](http://link.zhihu.com/?target=https%3A//arxiv.org/abs/1610.05755)
- GANs可以比完全明显的信念网络(NADE,PixelRNN,WaveNet等)更快的产生样本,因为它不需要在采样序列生成不同的数据.
- GANs不需要蒙特卡洛估计来训练网络,人们经常抱怨GANs训练不稳定,很难训练,但是他们比训练依赖于蒙特卡洛估计和对数配分函数的玻尔兹曼机简单多了.因为蒙特卡洛方法在高维空间中效果不好,玻尔兹曼机从来没有拓展到像ImgeNet任务中.GANs起码在ImageNet上训练后可以学习去画一些以假乱真的狗
- 相比于变分自编码器, GANs没有引入任何决定性偏置( deterministic bias),变分方法引入决定性偏置,因为他们优化对数似然的下界,而不是似然度本身,这看起来导致了VAEs生成的实例比GANs更模糊.
- 相比非线性ICA(NICE, Real NVE等,),GANs不要求生成器输入的潜在变量有任何特定的维度或者要求生成器是可逆的.
- 相比玻尔兹曼机和GSNs,GANs生成实例的过程只需要模型运行一次,而不是以马尔科夫链的形式迭代很多次.

**劣势**

- 训练GAN需要达到纳什均衡,有时候可以用梯度下降法做到,有时候做不到.我们还没有找到很好的达到纳什均衡的方法,所以训练GAN相比VAE或者PixelRNN是不稳定的,但我认为在实践中它还是比训练玻尔兹曼机稳定的多.
- 它很难去学习生成离散的数据,就像文本
- 相比玻尔兹曼机,GANs很难根据一个像素值去猜测另外一个像素值,GANs天生就是做一件事的,那就是一次产生所有像素, 你可以用BiGAN来修正这个特性,它能让你像使用玻尔兹曼机一样去使用Gibbs采样来猜测缺失值, 





















