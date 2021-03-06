# [Point2Node: Correlation Learning of Dynamic-Node for Point Cloud Feature Modeling](https://arxiv.org/abs/1912.10775)

## 背景
- 探索点云节点的自通道相关、局部相关、非局部相关信息
## 模型流程
![](p2n1.png)
- 首先采用`U-Net`结构的`X-Conv`作为`Feature Extraction`层提取每个点的高级表征`V^0`
- Dynamic Node Correlation (DNC) 模块获取节点的自相关、局部相关、非局部相关信息，其中局部与非局部相关层与上层信息做的跳跃连接利用AFA自适应特征聚合模块
- 全连接分类
### 自相关
![](f1.png)

![](f2.png)

![](f3.png)
- `y = x + a(x * softmax(MLP(x))) = x(1 + a * softmax(MLP(x)))`，利用`softmax`和`MLP`获得每个通道的权重（所有权重和为1），利用权重对每个通道进行缩放，可学习参数`a`控制缩放比例
### 局部相关
![](f4.png)
- 输入为局部点的隐向量`V∈[K, C]`, K代表邻居数，C代表特征通道，通过俩个不同的`MLP(θ、ϕ)`对`V`降维得到`Q、X`

![](f5.png)
- `m[K, K] = Q[K, C] ⊗ X^T[C, K]`：利用`Q`和`X`做矩阵乘法作为邻接矩阵`m`表示每个局部点与其他局部点的相关性

![](f6.png)
- 利用`softmax`对以每个局部点为中心针对其他局部点的相关权重做归一化

![](f7.png)
- 利用权重更新每个局部点

![](f8.png)
- `Max Pooling`聚合局部信息
### 非局部相关
- 放大版的局部注意力机制，把局部点换成全局重复局部相关相同操作
### 自适应特征聚合
- 这个模块主要是代替残差连接的，输入为做相关性聚合前的特征图`V`和之后的`V_up`

![](f13.png)
- 对所有节点`V[N, C]`做`Mean Pooling`得到全局特征`s[1, C]`

![](f14.png)

![](f15.png)
- 然后过`MLP`和`softmax`得到每个通道对聚合前后两种情况的权重`m1`和`m2`，此时`m1 + m2 = 1`，构成门控

![](f16.png)
- 按权相加
