# Q1: 在实际工作中，FM和MF哪个应用的更多，为什么?

FM的应用场景更多。因为MF只考虑了user与item两个特征维度，而现实中一个预测问题包含的特征维度可能很多。

因子分解机FM除了user与item两个特征，还引入了更多辅助信息作为特征，并可以进行2阶特征组合，因此FM的应用会更多。

# Q2: FFM与FM有哪些区别？

## A2:

+ FM算法每个特征只有一个隐向量，这个隐向量被用来学习与其他任何特征之间的影响。
+ FFM算法把相同性质的特征归于同一个field内，因此每个特征有多个隐向量，使用哪个，取决于和哪个向量进行点乘；
+ FM只是FFM的一个特例。

# Q3: DeepFM相比于FM解决了哪些问题，原理是怎样的？

## A3: 

FM可以做特征组合，但是计算量大，一般只考虑2阶特征组合。但DeepFM则可以实现高阶特征的组合。

DeepFM = FM + DNN，一阶和二阶特征组合由因子分解机FM完成；高阶特征组合通过神经网络DNN完成。

# Q4:Surprise工具中的baseline算法原理是怎样的？BaselineOnly和KNNBaseline有什么区别？

## A4: 

Baseline是基于模型的推荐中矩阵分解的算法，算法的思想就是设立基线，并引入用户的偏差以及item的偏差；它看的是某个用户与整体的差异。

**BaselineOnly**就是基于模型的baseline算法在surprise中的API。

surprise中的API：**KNNBaseline**是基于邻域的协同过滤算法，可以实现User-based和Item_based；它考虑了baseline算法。

# Q5:基于邻域的协同过滤都有哪些算法，请简述原理?

## A5:

以下4个基于邻域的协同过滤算法默认都是基于用户的协同过滤，当参数user_based=False时，是基于商品的协同过滤。

+ knns.KNNBasic 
  + 基本的协同过滤算法，预测值只考虑了用户 v 对物品 I 的兴趣$r_{vi}$；
    $$
    \hat{r_{ui}} = \frac{\sum_{v\epsilon N_{i}^{k}(u)}sim(u,v)·r_{vi}}{\sum_{v\epsilon N_{i}^{k}(u)}sim(u,v)}
    $$
    或者：
    $$
    \hat{r_{ui}} = \frac{\sum_{j\epsilon N_{u}^{k}(i)}sim(i,j)·r_{vi}}{\sum_{j\epsilon N_{u}^{k}(i)}sim(i,j)}
    $$
    
  
+ knns.KNNWithMeans

  + 考虑了每个用户的平均评分.
    $$
    \hat{r_{ui}} = \mu_{u} + \frac{\sum_{v\epsilon N_{i}^{k}(u)}sim(u,v)·(r_{vi} - \mu_{v})}{\sum_{v\epsilon N_{i}^{k}(u)}sim(u,v)}
    $$
    或者：
    $$
    \hat{r_{ui}} = \mu_i + \frac{\sum_{j\epsilon N_{u}^{k}(i)}sim(i,j)·(r_{uj} - \mu_j)}{\sum_{j\epsilon N_{u}^{k}(i)}sim(i,j)}
    $$
    

+ knns.KNNWithZScore

  + 考虑了每个用户的z分数归一化
    $$
    \hat{r_{ui}} = \mu_u + \sigma_u\frac{\sum_{v\epsilon N_{i}^{k}(u)}sim(u,v)·(r_{vi} - \mu_{v})/\sigma_v}{\sum_{v\epsilon N_{i}^{k}(u)}sim(u,v)}
    $$
    

    或者：
    $$
    \hat{r_{ui}} = \mu_i + \sigma_i\frac{\sum_{j\epsilon N_{u}^{k}(u)}sim(i,j)·(r_{uj} - \mu_{j})/\sigma_j}{\sum_{j\epsilon N_{u}^{k}(i)}sim(i,j)}
    $$
    

+ knns.KNNBaseline

  + 考虑了用户打分的偏差，偏差计算时使用baseline算法，在KNNWithMeans基础上，用baseline替代均值。
    $$
    \hat{r_{ui}} = b_{ui} + \frac{\sum_{v\epsilon N_{i}^{k}(u)}sim(u,v)·(r_{vi} - b_{vi})}{\sum_{v\epsilon N_{i}^{k}(u)}sim(u,v)}
    $$
    或者：
    $$
    \hat{r_{ui}} = b_{ui} + \frac{\sum_{j\epsilon N_{u}^{k}(i)}sim(i,j)·(r_{uj} - b_{uj})}{\sum_{j\epsilon N_{u}^{k}(i)}sim(i,j)}
    $$
    



