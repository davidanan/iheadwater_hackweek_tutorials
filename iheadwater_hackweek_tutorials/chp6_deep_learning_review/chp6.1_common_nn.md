# 深度学习常见算法及模型的简介

通过前一节的学习我们知道，深度学习的核心是让计算机自动学习各类算法，对大量样本数据进行分析并寻求规律，从而对未知数据进行预测。此过程与水文预报通过分析历史水文数据获取规律，并在其基础上概化模型预测水文过程高度一致，因此深度学习在水文领域获得了广泛的关注。本教程主要面向水文领域研究人员，系统地介绍深度学习水文预报中常见深度学习模型的原理与结构，深度学习水文预报模型一般构建方法以及深度学习与水文物理机制的整合方式。 前边的一节主要是讲的深度学习的一些常识，那么在本节当中，我们将能够学习到深度学习的一些基本算法结构以及常用的模型结构。

### 深度学习之神经网络的结构

在深度学习的空前发展影响下，深度学习可以应用在各大领域中，根据应用情况的不同，深度神经网络的形态也各不相同，现在机器学习中最为受欢迎的算法已经从SVM算法变为当今的神经网络，我们常常使用深度学习这个术语来指代神经网络训练的过程,特别是大规模的训练，那么神经网络是什么呢？神经网络为什么是这样的结构呢？神经元又是如何连接起来的？如何利用神经网络进行学习呢？相信阅读完下边的视频，我们的疑问就可以得到解决啦。相应视频链接为：<https://www.bilibili.com/video/BV1bx411M7Zx?vd_source=c766b103a42723692760409937dfbe92>

### 深度学习之梯度下降法

在了解完神经网络的基本概念以及作用原理之后，我们再来学习下梯度下降法，梯度下降法（Gradient Descent Optimization）是神经网络模型训练最常用的优化算法，对于深度学习模型，基本都是采用梯度下降法来进行优化训练，它不仅是神经网络学习的基础，机器学习中很多其他技术也是基于这个方法。下边的视频主要是介绍了什么是梯度下降法？神经网络是怎么学习的？神经网络的能力以及隐含层神经元的真实的目的是什么？另外通过这个视频，我们还可以学习一些深度学习方面的术语，偏置值的含义等。
相应的视频链接为：<https://www.bilibili.com/video/BV1Ux411j7ri?vd_source=c766b103a42723692760409937dfbe92>

### 深度学习之反向传播

反向传播（英语：Backpropagation，缩写为BP）是“误差反向传播”的简称，是一种与最优化方法（如梯度下降法）结合使用用来训练人工神经网络的常见方法。该方法计算网络中所有权重计算损失函数的梯度，这个梯度会反馈给最优化方法，用来更新权值以最小化损失函数，深度学习的核心便是反向传播算法，它算的是单个训练样本想怎么修改权重与偏置，不仅是说每个参数应该变大还是变小，还计算了这些变化的比例是多大，怎样才能最快的降低代价。那么如何更加直观的理解反向传播？以及反向传播的原理是什么？
怎么反向应用链式法则来计算代价函数对之前的权重和偏置的敏感度？让我们通过下边的视频来寻找答案吧。

https://www.bilibili.com/video/BV16x411V7Qg?p=2&vd_source=c766b103a42723692760409937dfbe92

## 常见的深度学习模型

在学习完深度学习常用的几种算法后，我们接着向下学习深度学习中常见的几种学习模型。

### 卷积神经网络

卷积神经网络（Convolutional Neural Network, CNN）是一类使用卷积运算代替全连接矩阵乘法的神经网络，是深度学习的代表模型之一。它能够将大数据里的图片有效的降维成小数据量(并不影响结果)，同时也能够保留图片的特征。CNN由输入层、卷积层、池化层、全连接层及输出层构成，其模型结构如下：

![](../img/CNN.png)

- 卷积层 – 主要作用是保留图片的特征；

- 池化层 – 主要作用是把数据降维，减少网络中参数的数量，可以有效的避免过拟合；

- 全连接层 – 根据不同任务输出我们想要的结果。

通过这种结构设计，CNN克服了MLP难以处理高维复杂时空模式数据的缺点，CNN需训练参数减少，降低了网络模型复杂度，使得模型更容易训练，同时，CNN能获取到一系列输入数据时空维度局部特征，最后再经过全连接层汇总，从而有效地挖掘高维数据的时空模式。

### 循环神经网络与LSTM神经网络

循环神经网络（Recurrent Neural Network, RNN）是一种有效处理序列数据的算法，之所以他能处理序列数据，是因为在序列中前面的输入也会影响到后面的输出，相当于有了“记忆功能”。RNN同样包含输入层、隐含层、输出层。其能用于建模动态系统，但反向传播计算中梯度的连乘效应会导致梯度消失和爆炸问题，使得其无法处理很长的输入序列。长短期记忆（Long Short-Term Memory, LSTM）神经网络是一种递归神经网络，包括长时间储存信息的专用记忆单元，该模型建立了称为“门”的内部处理单元作为记忆模块，来实现序列信息的有效存储和更新。LSTM不存在梯度消失的问题，这就使得它们可以学习输入和输出特征之间的长期依赖关系，其有单元状态和隐含状态两个传输状态，单元状态随时间缓慢改变，而不同时刻的隐含输出可能会很不同。我们可以将循环神经网络结构与LSTM神经网络计算过程归结为一张图，如下：

![](../img/RNN.png)

## LSTM与CNN在水文中的研究与应用

水文预报是典型的时间序列预测问题，且一些变量之间存在较长时期的依赖关系，比如流域退水过程、积雪对径流的影响等，而LSTM能处理序列内单元之间彼此有复杂关联的任务。常见的应用包括降水预报、径流预报、洪水预报、土壤含水量时空分布预测、地下水位及流量模拟、水库水位出流预测、水质分析预测等多方面。此外，将多时刻的水文网格数据连接一起可构成视频信息，结合CNN和LSTM能构建提取复杂时空特征的深度神经网络应用于水文预报。

总而言之，深度学习已经成为了机器学习研究中的一个新的发展热点。基于水文数据的大量性和水文原理的复杂性,掌握深度学习技术可对水文数据进行有效模拟,对水文工作起到指导作用。



