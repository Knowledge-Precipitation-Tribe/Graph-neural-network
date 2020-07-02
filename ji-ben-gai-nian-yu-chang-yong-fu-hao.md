# 基本概念与常用符号

## 图



![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/graph.png)

图是一种数据结构，由顶点集$$V$$和边集$$E$$组成,表示为$$G=(V,E)$$，其中$$v_{i} \in V$$代表每个顶点，$$e_{i j}=\left(v_{i}, v_{j}\right) \in E$$代表表每条边。

## 有向图与无向图

### 有向图



### 无向图

## 加权图与非加权图

### 加权图

### 非加权图



## 连通图与非连通图

### 连通图

### 非连通图

## 二部图



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



## 其他相关概念

![](https://camo.githubusercontent.com/d04233f2b375039a8d60078fb67eb09dd0c3abc6/68747470733a2f2f63646e2e6d6174687069782e636f6d2f736e69702f696d616765732f37477848384b436d437455795f4f3349556f566236356975535a6d524346334c446e444b5144724e5637452e6f726967696e616c2e66756c6c73697a652e706e67)

