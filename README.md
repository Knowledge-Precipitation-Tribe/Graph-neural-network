# Graph-neural-network
图神经网络从入门到精通

## 阅读指南

1. 在线观看请使用Chrome浏览器，并安装插件：[MathJax Plugin for Github(需科学上网)](https://chrome.google.com/webstore/detail/mathjax-plugin-for-github/ioemnmodlmafdkllaclgeombjnmnbima)， 插件[Github地址](https://github.com/orsharir/github-mathjax)
2. 或下载内容到本地，使用markdown相关软件打开，如：[Typora](https://typora.io/)

## 文章列表

- <a href = "#参考文献">参考文献</a>
- <a href = "#1. 基本概念与常用符号">1. 基本概念与常用符号</a>
- <a href = "#易混淆概念">易混淆概念</a>
  - <a href = "#图神经网络与图嵌入">图神经网络与图嵌入</a>

## [1. 基本概念与常用符号](#content)

### 1.1 图

<div align = "center"><image src="https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/blob/master/images/graph.png" width = "300" height = "200" alt="axis" align=center /></div>

图是一种数据结构，由顶点集$$V$$和边集$$E$$组成,表示为$$G=(V,E)$$，其中$$v_{i} \in V$$代表每个顶点，$$e_{i j}=\left(v_{i}, v_{j}\right) \in E$$代表表每条边，图分为两种：

- 有向图：每条边都带有方向
- 无向图：每条边都不带有方向，上图就是一个无向图

### 1.2 顶点的度

与顶点$$V$$相关的边的条数称为顶点$$V$$的度。

### 1.3 图的表现形式

#### 1.3.1 邻接矩阵

邻接矩阵是表示顶点之间相邻关系的矩阵。设$$G=(V,E)$$是具有$$n$$个顶点的图，顶点序号依次为$$0,1,...,n-1$$,则$$G$$的邻接矩阵是具有如下定义的$$n$$阶方阵$$A$$：

- $$A[i][j]=1$$表示顶点$$i$$与顶点$$j$$邻接，即$$i$$与$$j$$之间存在边
- $$A[i][j]=0$$表示顶点$$i$$与顶点$$j$$不邻接，即$$i$$与$$j$$之间没有边

<div align = "center"><image src="https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/blob/master/images/adjMatrix.png" width = "300" height = "200" alt="axis" align=center /></div>

#### 1.3.2 度矩阵

度矩阵其中包含的信息为的每一个顶点的度数，度矩阵$$D$$:

<div align = "center"><image src="https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/blob/master/images/degreeMatrix.png" width = "300" height = "200" alt="axis" align=center /></div>

#### 1.3.3 拉普拉斯矩阵

给定一个有$$n$$个顶点的图 $$G=(V,E)$$，其拉普拉斯矩阵被定义为$$ L = D-A$$，$$D$$其中为图的度矩阵，$$A$$为图的邻接矩阵，拉普拉斯矩阵$$L$$:

<div align = "center"><image src="https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/blob/master/images/degreeMatrix.png" width = "300" height = "200" alt="axis" align=center /></div>

## [易混淆概念](#content)

### [图神经网络与图嵌入](#content)

#### 图嵌入

将网络中的节点表示为低维向量表示，同时保留网络拓扑结构和节点内容信息，将获得的嵌入向量用于分类，聚类等问题中。

#### 图神经网络

将获得的嵌入向量用于分类，聚类等问题中

#### 两者主要区别

GNN是一组为解决各种任务而设计的神经网络模型，GNN是一组为解决各种任务而设计的神经网络模型。<br>

图嵌入是针对同一种任务的各种方法，图嵌入也包含非深度学习的方法，例如矩阵分解以及随机游走等。

## [参考文献](#content)

[1] THUNLP: [GNNpapers](https://github.com/thunlp/GNNPapers)

[2] [A Comprehensive Survey on Graph Neural Networks](https://arxiv.org/pdf/1901.00596.pdf)

