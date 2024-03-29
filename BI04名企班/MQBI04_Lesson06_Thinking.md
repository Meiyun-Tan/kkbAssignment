# Q1:什么是近似最近邻查找，常用的方法有哪些？

## A1:

+ ANN，Approximate Nearest Neighbor，近似最近邻检索，在牺牲可接受范围内的精度的情况下提高检索效率。在对庞大的数据量以及数据库中高维的数据信息进行检索时仍能保持可接受的检索时间和检索效果。
+ 常用方法:
  + MinHash，适用于短文本。将每篇文档用出现1次或多次的k-shingle的集合表示；最小哈希值计算的是特征矩阵按行进行随机排列后，每列第一个行值为1的行的行号构成一个Signature；文档向量想要降到几维就进行多少次随机置换，每次置换后使用MinHash得到Signature矩阵，使用Sig矩阵相似度来近似估计原始矩阵的Jaccard相似度。MinHash算法使用行号打擂法对数据进行排序，hash变换后比较新行号与老行号的大小，小则更新，大则不更新，从而节省存储空间和计算时间。
  + MinHashLSH，适用于短文本。在MinHash基础上，将Signature向量分成多段(band)，即：分成b组，每组由r行组成；对每一组进行hash，各个组设置不同的桶空间。只要两列有一组的MinHash相同 ，那么这两列就会hash到同一个桶而成为候选项。
  + MinHashLSHForest，局部敏感随机投影森林。
    + 一棵随机投影树的建立步骤：随机选取一个从原点出发的向量，与这个向量垂直的直线把平面内的点一分为二，当点数量比较大的时候，继续划分；再随机选取一个向量，重复上述步骤。一直划分，直到每个叶子节点中点的数量足够小，即：将每次搜索与计算的点的数量减小到一个可接受的范围，就建成一棵随机投影树；
    + 建立多个随机投影树构成随机投影森林，将森林的综合结果作为最终的结果。
    + 支持返回top-k个近似邻居。
  + MinHashLSHEnsemble，计算相似度时，对大的集合进行惩罚，计算的是交集元素个数与自己集合元素总数的比， $containment = \frac{|Q \cap X|}{|Q|}$ 。
  + SimHashLSH，适用于长文本。
    + 汉明距离指两个二进制串中不同位的数量；
    + 向量相似度越高，对应的汉明距离越小；
    + 通过SimHash算法得到每篇文档的指纹，计算2个文档指纹的汉明距离，通常2篇文档汉明距离在3以内，则认为相似度比较好。

# Q2:为什么两个集合的minhash值相同的概率等于这两个集合的Jaccard相似度?

## A2:

+ 对于列C1和列C2，每一行的元素可以分为以下3类：
  
  a. 两列值都为1，比如：两列中都有元素‘g’；
  
  b. 其中一列的值为0，另外一列为1，代表只有一列中有元素‘g’；
  
  c. 两列的值都为0，代表2列中均没有出现元素‘g’；
  
+ 文档中出现相同文本的文本越多，则2个文档越相似，因此c类的情况对我们统计文档相似度没有意义，因此$C_1$, $C_2$的MinHash相等的概率：P($h(C_1) = h(C_2)$) = P(删掉c类后，第一个为a类的行号) = a类行的个数/所有行的个数 = a / (a+b) 

+ Jaccard相似度：计算交比并，即： 2个集合S1和S2中交集的元素个数比上2个集合的并集的元素个数。
  
  + 公式：

$$
Jac(X, Y) = \frac{|S_1 \cap S_2|}{|S_1 \cup S_2|}
$$

​	对于列C1和列C2，$C_1 \cap C_2$即为a类的行数，而$C_1 \cup C_2$即为b类的行数，因此两个集合的minhash值相同的概率等于这两个集合的Jaccard相似度。

# Q3:SimHash在计算文档相似度的作用是怎样的？

SimHash使用汉明距离来计算2个向量间的相似度。

SimHash算法的步骤：

1. 首先综合考虑储存成本以及数据集的大小，设置一个合理的SimHash的位数，比如:32位；
2. 然后初始化SimHash，让各位初始化为0；
3. 采用k-Shingles 提取文本中的特征，其中k>=2，即至少采用2-Shingles来构建文本集合；
4. 使用传统的hash函数计算每个word的hashcode，我的理解是Python里对应的`hash()`函数所返回的哈希值的结果的二进制码；
5. 对每个word的二进制hashcode的每一位，如果该位为1，则simhash相应位的值加它的权重(权重值通常是出现的概率)，否则减它的权重；
6. 计算最后得到的32位的SimHash，如果这位大于0，则设为1，否则设为0；
7. 通过前6步，利用SimHash算法得到每篇文档的指纹；
8. 然后计算2个文档指纹的汉明距离，如果距离在3以内，就认为相似度比较高；
9. 当面对海量文档时，比如：10亿文档($2^{34}$)，假设SimHash签名为64位，且我们认为2个文档汉明距离在3以内就相似；则我们可以通过抽屉原理，将64位分成4段(64/4=16)，每段16位，只要2个文档其中一段SimHash相等，则2个文档的汉明距离将会在3以内，我们就可以认为2个文档相似；
10. 采用索引方式进行查找加速，取出每一段相同的候选文本；
11. 通过以上方式，可以大大的降低计算时间。如步骤9的例子：虽然文档中有$2^{34}$个签名矩阵，但实际匹配上每段的结果最多只有$2^{34-16} = 262144$个，4个段返回的结果总数只有大概100万(4*262144)，也就是说，原本需要比较10亿次汉明距离，使用SimHash算法只需要比较100万次就可以了。

# Q4:为什么YouTube采用期望观看时间作为评估指标

## A3:

+ 原因如下：
  + YouTube的利润来源主要来自视频广告，而广告的曝光机会与用户观看时长成正比 ，因此用户观看时长这个指标对YouTube尤为重要。(From:《深度学习推荐系统》)
  + 不同的用户所观看的视频数量可能会不同，观看时长也会不同，所以为了用统一的架构来表示，故而用平均值来表示更准确些。
  + CTR指标对视频搜索具有一定的欺骗性，因此选择期望观看时间作为评估指标。

