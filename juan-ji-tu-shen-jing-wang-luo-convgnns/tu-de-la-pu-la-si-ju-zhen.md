# 图的拉普拉斯矩阵

## 拉普拉斯矩阵

拉普拉斯矩阵\(Laplacian Matrix\)是用来研究图的结构性质的核心对象，给定一个具有$$n$$个顶点的图$$G=(V,E)$$，其拉普拉斯矩阵被定义为$$L=D-A$$，$$D$$为图的度矩阵，$$A$$为图的邻接矩阵。

例如下图所示的图结构

![](../.gitbook/assets/image%20%286%29.png)

那么它的拉普拉斯矩阵$$L$$为:

![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/laplaMatrix.png)

## 归一化拉普拉斯矩阵

归一化的拉普拉斯矩阵定义为$$\mathbf{L}=\mathbf{I}{\mathbf{n}}-\mathbf{D}^{-\frac{1}{2}} \mathbf{A} \mathbf{D}^{-\frac{1}{2}}$$。

