# Q1: 电商定向广告和搜索广告有怎样的区别，算法模型是否有差别

## A1:

+ 定向广告有2种页面：千人千面和千人十面；
+ 电商定向广告和搜索广告二者的区别：
  + 用户没有明显的意图（不主动Query查询）
  + 用户来淘宝之前，自己没有特别明确的目标，需要利用以往的历史行为进行item推荐；
  + 因此，定向广告需要考虑的样本特征更多和历史相关。
+ 算法模型它们本质上都属于CTR模型，深度学习模型都用到了Embedding；最大的区别在于，定向广告推荐应用的典型模型是带Attention机制的DIN模型（Deep Interest Network，深度兴趣网络）、DIEN模型（Deep Interest Evolution Network）和DSIN模型（Deep Session Interest  Network）；



# Q2: 定向广告都有哪些常见的使用模型，包括Attention机制模型？

## A2:

包括Attention机制的模型：

+ DIN模型（Deep Interest Network 深度兴趣网络）：

  在对用户兴趣的表示上引入了attention机制，即对用户的每个兴趣表示赋予不同的权值，这个权值是由用户的兴趣和待估算的广告进行匹配计算得到的

+ DIEN模型（Deep Interest Evolution Network 深度兴趣进化网络）：

  + 输入层，user profile，ad，context这三类特征的低维嵌入向量的学习（与base model处理相同）
  + 使用behavior layer，interest extractor layer 以及 interest evolving layer从用户历史行为中挖掘用户与目标商品相关的兴趣及演变
  + 目标损失函数，采用负对数似然（negative log-likelihood loss ）

+ DSIN模型（Deep Session Interest  Network 深度会话兴趣网络）：

  + 将用户的连续行为自然地划分为Session，通过带有偏置编码的self attention网络对每个会话进行建模
  + 使用BI-LSTM捕捉用户不同历史会话兴趣的交互和演变
  + 设计了两个Activation Unit，将它们与目标item聚合起来，形成行为序列的最终表示形式（黄色，蓝色）



# Q3: DIN中的Attention机制思想和原理是怎样的?

## A3:

**“注意力机制”**来源于人类天生的“选择性注意”的习惯。

它模拟了人类最自然，最发自内心的注意力行为特点，使得推荐系统更加接近用户真实的思考过程，从而达到提升推荐效果的目的。

+ **Attention机制思想：**

  + 在pooling的时候，与候选广告集相关的商品权重大一些，不相关的商品权重小一些；
  + 主要思想是在对用户兴趣的表示上引入了attention机制，即它用户历史行为待征进行 embedding操作，视为对用户兴趣的表示，之后通过 Attention Unit，对每个兴趣表示赋予不同的权重。这个权重是由用户的兴趣和待估算的广告进行匹配计算得到的。

+ **Attention机制的原理：**

  + DIN 的基础模型 Base Model是一个典型的Embedding结构，它的输入特征有用户属性特征（User Proflie Features）、用户行为特征（User Behaviors）、候选广告特征（Candidate Ad）和场景特征（Context Features）；

  + 把ID特征转换成对应的 Embedding，然后把这些 Embedding 连接起来组成当前商品的 Embedding；

  + 与 Base Model 相比，DIN 为每个用户的历史购买商品加上了一个激活单元（Activation Unit），这个激活单元生成了一个权重，这个权重就是用户对这个历史商品的注意力得分，权重的大小对应用户注意力的高低；

  + 通过SUM Pooling 层把带权重的商品的 Embedding 叠加起来，然后再把叠加后的 Embedding 跟其他所有特征的连接结果输入 MLP；

    



# Q4: DIEN相比于DIN有哪些创新?

## A4:

DIEN 模型弥补了 DIN 模型没有对行为序列进行建模的缺陷，它围绕兴趣进化这个点进一步对 DIN 模型做了改进。主要以下创新：

+ 通过引入序列模型 AUGRU 模拟了用户兴趣进化的过程；

+ 在 Embedding layer 和 Concatenate layer 之间加入了生成兴趣的 Interest Extractor Layer 和模拟兴趣演化的 Interest Evolving layer
  Interest Extractor Layer ；

  + **Interest Extractor Layer** 兴趣抽取层使用了GRU的结构抽取了每一个时间片内用户的兴趣；
    + 具体地，作者加入了一个二分类模型来计算兴趣抽取的准确性，选取下一个行为作为正样本，也从未点击的样本中选取一个作为负样本，别与抽取出的兴趣表征结合输入到设计的辅助网络中，得到预测结果，并通过logloss计算辅助网络的损失。

  + **Interest Evolution Layer** 兴趣演化层， 利用序列模型 AUGRU 的结构将不同时间的用户兴趣串联起来，形成兴趣进化的链条

+ 最终把当前时刻的“兴趣向量”输入上层的多层全连接网络，与其他特征一起进行最终的 CTR 预估
+ DIN中简单的使用外积完成的activation unit  =>  DIEN使用attention-based GRU网络，更好的挖掘序列数据中的兴趣及演化



# Q5: DSIN关于Session的洞察是怎样的，如何对Session兴趣进行表达?

## A5:

DSIN利用用户行为序列中的多个历史会话，一个session是在给定的时间范围内发生的交互列表（用户行为列表）；

表达方法：

+ 每个session中的行为是相近的，而在不同会话之间差别是很大的（类似于聚类），即：用户的行为序列可以用一个个session序列表示，session内的用户兴趣变化不大；
+ 和airbab一样，即：将用户的点击行为按照时间排序，前后的时间间隔大于30分钟，算成另外一个session。
+ self-attention用于提取一个session内的用户兴趣



# Q6: 如果你来设计淘宝定向广告，会有哪些future work（即下一个阶段的idea）

## A6:

1. 加入对评价的利用：

用户购买商品并确认收货后，存在几种可能：

+ 不评价，默认好评；
+ 对商品满意，体现在好评或正面评论内容中；
+ 对商品或商家不满意、给中差评，或评论内容负面；

可见，用户购买该商品后，并不一定代表他喜欢该商品，所以我们在做推荐时，可以加入评价的作用，降低用户虽然购买但实际并不满意的商品的推荐权重。

2. 加入对商品使用周期的利用
   + 基于该品类下用户复购商品的平均周期，作为该商品的寿命周期，用户下单后短期内不推荐该类商品；在寿命周期临近一周时，开始推荐该商品；
   + 还可以进一步优化，计算出不同用户群体的复购周期，从而对不同用户群体使用不同的推荐周期。
