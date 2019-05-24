# 🗃 AI-Paper-Drawer
人工智能论文关键点概括集结。This project aims to collect key points of AI papers. 扫码加入QQ交流群 ↓


![](drawer/home.png)

此 repo 旨在记录各 AI 论文的精简概括，以便大家更好地掌握不同邻域的发展脉络。

# 子抽屉
[图神经网络](图网络专区.md)

# 🗡 论文共读讨论组（下次重建时间：2019/06/01）
本活动的宗旨只有一个：让所有成员在组内进步得比在组外更**快**更稳 ⚡
活动规则：
- 在大群的基础之上，本群每个月会维护一个额外的讨论组。
- 申请进组的成员必须在每次申请时提供至少**一篇**论文的概要，且**有义务回答**组内所有成员对于该论文的问题。
  - 论文主题需要跟人工智能高度相关，但不限制研究邻域
  - 提供的概要包括：
    a. 论文地址（如 arXiv 的 URL）
    b. 发表年份
    c. 所在期刊（如 NeurIPS、CVPR、arXiv）
    d. 针对的领域（比如图片分类、语义分割等）
    e. 模型流程或论文主要贡献
    d. 模型示意图（可选）
  - 所提供的概要**必须精简**，即以最少的语句（几句话）概括流程
  - 这意味着您必须对所概括论文的模型原理**理解程度达到 90% 以上**，但实验、相关工作、代码部分不做要求
  - 所有组员需要对一篇论文负责，并有义务回答或共同探讨组内不同成员的提问（对单一成员，有义务回答2个问题），责任持续至小组解散（一般一月解散一次）
  - 组内会有表格记录每一期所有成员负责的论文
- 所提供的概要将被记录在 Github 上（就在下面），推荐推 PR 以便记录贡献人信息。也可以直接提交材料至群主获得入组资格。
- 所提供的概要不限出处，但您需要对其进行约简，且需达到对于模型原理的高度理解，否则可能被请出。
- 讨论组以一月为限，至每月月初将解散从建，在此之后您无需再对所提供论文提供解答。
- 以上所提要求目的在于维护组内所有成员共同利益，如有建议或意见，恭请指教。
独木不成林，独林不成森 🌴。参加本活动意味着**以一篇论文换取多篇论文的深度专人解析**，希望所有加组成员各取所需，共同进步。
拒绝伸手党，论文共读讨论组期待您的到来~ ⛄

# Graph

# CV
## 2017
### [【CVPR】](https://arxiv.org/abs/1612.00593) PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation
![](drawer/PointNet.png)
- 点云分类/语义分割
- 利用核长为1的卷积对每个点单独升维后使用对称函数（本文利用MaxPooling）获取具有输入排列不变性的全局点云特征。
  - 分类：使用全连接网络对全局特征降维至类别数。
  - 语义分割：在每个升维后的点特征向量（1024维）后拼接上全局特征，再使用单一感受野的卷积降维对每个点做分类。
- T-Net：使用如上操作提取固定多个全局特征构成变换矩阵，左乘点云数据施加线性变换，增加对点云刚性变换的鲁棒性。

# NLP

# Others
