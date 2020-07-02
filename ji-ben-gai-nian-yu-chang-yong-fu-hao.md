# 基本概念与常用符号

## 图



![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/graph.png)

图是一种数据结构，由顶点集$$V$$和边集$$E$$组成,表示为$$G=(V,E)$$，其中$$v_{i} \in V$$代表每个顶点，$$e_{i j}=\left(v_{i}, v_{j}\right) \in E$$代表表每条边。

## 有向图与无向图

### 有向图

如果图中的边存在方向性，则称这样的边为有向边，包含有向边的图成为有向图。

![](.gitbook/assets/image%20%281%29.png)

### 无向图

无向图中的边都是没有方向的。



![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/graph.png)

## 加权图与非加权图

### 加权图

图中的每条边都有一个实数与之相对应，称这样的图为加权图。在世纪场景中，权重可以代表距离或者两人之间的相似程度等，一般情况下认为各边上的权重代表定点之间的连接强度。

![](.gitbook/assets/image%20%282%29.png)

### 非加权图

非加权图与加权图相对应，非加权图认为各边上的权重是一样的。

## 连通图与非连通图

### 连通图

如果图中不存在任何孤立的结点，称这样的图为连通图。

### 非连通图

如果图中存在孤立的结点，称这样的图为非连通图。

## 二部图/二分图

![](.gitbook/assets/image%20%283%29.png)

二部图是一类特殊的图，设$$G=(V,E)$$是一个无向图，如果顶点$$V$$可分割为两个互不相交的子集$$(A,B)$$，并且图中的任意一条边$$e_{ij}$$均有$$vi \in A$$，$$v_j \in B$$或者$$vi \in B$$，$$v_j \in A$$，则称图G为一个二分图。二部图是一种十分常见的图数据结构，描述两类对象之间的交互关系，比如：用户和商品，作者与论文

## 邻居

如果存在一条边连接定点和，则称是的邻居，反之亦然。

## 顶点的度

与顶点$$V$$相关的边的条数称为顶点$$V$$的度。

## 图的表现形式

### 邻接矩阵

邻接矩阵是表示顶点之间相邻关系的矩阵。设$$G=(V,E)$$是具有$$n$$个顶点的图，顶点序号依次为$$0,1,...,n-1$$,则$$G$$的邻接矩阵是具有如下定义的$$n$$阶方阵$$A$$：

* $$A[i][j]=1$$表示顶点$$i$$与顶点$$j$$邻接，即$$i$$与$$j$$之间存在边
* $$A[i][j]=0$$表示顶点$$i$$与顶点$$j$$不邻接，即$$i$$与$$j$$之间没有边

![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/adjMatrix.png)

### 度矩阵

度矩阵其中包含的信息为的每一个顶点的度数，度矩阵$$D$$:

![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/degreeMatrix.png)

### 拉普拉斯矩阵

给定一个有$$n$$个顶点的图$$G=(V,E)$$，其拉普拉斯矩阵被定义为$$L=D-A$$，$$D$$其中为图的度矩阵，$$A$$为图的邻接矩阵，拉普拉斯矩阵$$L$$:

![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/laplaMatrix.png)

### 关联矩阵

![](.gitbook/assets/image%20%284%29.png)

关联矩阵$$B$$的定义如下

$$
B=\left\{\begin{matrix}
1 & if \; v_i \; connect \; e_j\\ 
0 & else
\end{matrix}\right.
$$

用关联矩阵存储图时，我们需要两个一维数组分别表示定点集合和边集合，需要一个二维数组表示关联矩阵。

## 其他相关概念

![](https://camo.githubusercontent.com/d04233f2b375039a8d60078fb67eb09dd0c3abc6/68747470733a2f2f63646e2e6d6174687069782e636f6d2f736e69702f696d616765732f37477848384b436d437455795f4f3349556f566236356975535a6d524346334c446e444b5144724e5637452e6f726967696e616c2e66756c6c73697a652e706e67)

