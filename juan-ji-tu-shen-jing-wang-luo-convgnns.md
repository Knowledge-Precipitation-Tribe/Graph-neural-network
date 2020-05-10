# 卷积图神经网络ConvGNNs

卷积图神经网络（ConvGNNs）概括了从网格数据到图数据的卷积操作。主要思想是通过汇总节点自身的特征 $$ \mathbf{X}{v} $$ _和邻居的特征_ $$ \mathbf{X}{u} $$ 来生成节点$$v$$的表示形式，其中$$ u \in N(v) $$。与RecGNN不同，ConvGNN堆叠多个图卷积层以提取高级节点表示。ConvGNN在建立许多其他复杂的GNN模型中起着核心作用。

## 动态理解图卷积

第一步：每一个节点将自身的特征信息经过变换后发送给邻居节点。这一步是在对节点的特征信息进行抽取变换。

![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/GCN1.gif)

第二步：每个节点将邻居节点的特征信息聚集起来。这一步是在对节点的局部结构信息进行融合。 

![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/GCN2.gif)

第三步：把前面的信息聚集之后做非线性变换，增加模型的表达能力。

![](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/GCN3.gif)

通过图卷积操作就类似于正常的网格卷积，随着层数的增加会逐渐增加感受野的大小

![axis](https://github.com/Knowledge-Precipitation-Tribe/Graph-neural-network/raw/master/images/GCN4.gif)

## 基于频谱的卷积

基于谱的方法通过从图信号处理的角度引入filter来定义图卷积，其中图卷积运算被解释为从图信号中去除噪声。基于频谱的图卷积认为**图是无向的**，这样可以将无向图表示为**归一化的图拉普拉斯矩阵**，定义为$$\mathbf{L}=\mathbf{I}{\mathbf{n}}-\mathbf{D}^{-\frac{1}{2}} \mathbf{A} \mathbf{D}^{-\frac{1}{2}}$$_，其中_$$\mathbf{D}$$_代表无向图的_[_度矩阵_](ji-ben-gai-nian-yu-chang-yong-fu-hao.md#du-ju-zhen)_，因为归一化的图拉普拉斯矩阵是实对称半正定矩阵，所以可以将其分解为_$$\mathbf{L}=\mathbf{U} \mathbf{\Lambda} \mathbf{U}^{T}$$_，其中_$$\mathbf{U}=\left[u_0, u_1, \cdots, u_{n-1}\right] \in \mathbf{R}^{n \times n}$$是按照特征值排序的特征向量矩阵，$$\mathbf{\Lambda}$$是特征值的对角矩阵$$\boldsymbol{\Lambda}_{i i}=\lambda_{i}$$，归一化的拉普拉斯矩阵的特征向量就形成了一个正交空间，数学表示为：$$\mathbf{U}^{T} \mathbf{U}=\mathbf{I}$$。接下来是[图的傅立叶变换](https://zh.wikipedia.org/wiki/%E5%9C%96%E8%AB%96%E5%82%85%E7%AB%8B%E8%91%89%E8%BD%89%E6%8F%9B)，其实我们刚才得到的$$\mathbf{U}^{T}$$就是图的**傅立叶转换矩阵**。我们先将图节点的所有特征用向量表示为$$\mathbf{X}$$，其中$$\mathbf{X} \in \mathbf{R}^{n}$$，$$\boldsymbol{x}_i$$_代表第_$$i^{t h}$$_个节点，假如每个节点有5个特征，10个节点的话_$$\mathbf{X}$$_就是一个10\*5的矩阵。接下来我们就可以将图的傅立叶变化定义为：_$$\mathscr{F}(\mathbf{x})=\mathbf{U}^{T} \mathbf{x}$$_，得到的输出值为_$$\hat{\mathbf{X}}$$_，则逆傅立叶变换为：_$$\mathscr{F}^{-1}(\hat{\mathbf{x}})=\mathbf{U} \hat{\mathbf{x}}$$_。那么现在我们就可以把输入信号表示为：_$$\mathbf{x}=\sum_{i} \hat{x}_{i} \mathbf{u}_{i}$$。现在一个输入信号为$$\mathbf{X}$$，filter为$$\mathbf{g} \in \mathbf{R}^{N}$$的图卷积操作我们就可以定义为： 

$$
\begin{aligned}
\mathbf{x} *_{G} \mathbf{g} &=\mathscr{F}^{-1}(\mathscr{F}(\mathbf{x}) \odot \mathscr{F}(\mathbf{g})) \\
&=\mathbf{U}\left(\mathbf{U}^{T} \mathbf{x} \odot \mathbf{U}^{T} \mathbf{g}\right)
\end{aligned}
$$

_其中_$$\odot$$_表示_[_Hadamard product_](https://blog.csdn.net/BVL10101111/article/details/53066593)_，如果我们将过滤器表示为_$$\mathbf{g}{\theta}=\operatorname{diag}\left(\mathbf{U}^{T} \mathbf{g}\right)$$，那么基于频谱的图卷积可以简化为： 

$$
\mathbf{x} *_{G} \mathbf{g}_{\theta}=\mathbf{U g}_{\theta} \mathbf{U}^{T} \mathbf{x}
$$

这个就是基于频谱的图卷积的基本定义，关键的不同就在于filter：$$\mathbf{g} \theta$$的选择。

基于频谱的卷积神经网络假设filter：$$\mathbf{g}{\theta}=\mathbf{\Theta}_{i, j}^{(k)}$$是一个可学习的参数集合并考虑了具有多个通道的图形信号。那么基于频谱的图卷积我们就可以定义为： 

$$
\mathbf{H}_{i, j}^{(k)}=\sigma\left(\sum_{i=1}^{f_{k-1}} \mathbf{U} \Theta_{i, j}^{(k-1)} \mathbf{U}^{T} \mathbf{H}_{i, i}^{(k-1)}\right) \quad\left(j=1,2, \cdots, f_{k}\right)
$$

其中$$k$$代表层的索引，$$\mathbf{H}^{(k-1)} \in \mathbf{R}^{n \times f_{k-1}}$$是输入的图信号，$$\mathbf{H}^{(0)}=\mathbf{X}$$，$$f_{k-1}$$是输入的通道数，$$f_{k}$$是输出的通道数，是$$\Theta_{i, j}^{(k-1)}$$一个带有可学习参数的对角矩阵，由于拉普拉斯矩阵的特征分解，频谱卷积面临三个限制：

* 对图的任何扰动都会导致正交空间的变化
* 学习的filter是取决于域的，这意味着它们不能应用于具有不同结构的图
* 特征分解需要$$ O\left(n^{3}\right) $$的激计算复杂度

接下来我们就使用一些方法使得计算复杂度降到 $$O\left(m\right) $$.

#### **切比雪夫多项式近似**

通过一个GCN层就可以获得2个深度的邻居信息

#### **一阶近似**

通过3个GCN层也可以得到2个深度的邻居信息

## 基于空间的卷积

