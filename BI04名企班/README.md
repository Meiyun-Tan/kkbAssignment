# 名企BI04期 + 名企课 + 谭美云

---



# 20. 个性化推荐与金融数据分析

+ push date: 2021/2/21

+ Thinking: [MQBI04_Lesson20_Thinking.md](./MQBI04_Lesson20_Thinking.md)

+ Action1: 信用卡违约率检测

  + 主要工具：Pandas、pandas_profiling、sklearn
  + 主要技术：Pipeline、GridSearchCV、机器学习模型（SVC等）

  [MQBI04_Lesson20_Action1_GridSearchCV_CreditCardClients.ipynb](./MQBI04_Lesson20_Action1_GridSearchCV_CreditCardClients.ipynb)

+ 信用卡欺诈分析：

  + 主要工具：Pandas、pandas_profiling、sklearn
  + 主要技术：Pipeline、GridSearchCV、LogisticRegression、可视化

  [MQBI04_Lesson20_Action2_GridSearchCV_CreditCardFraud.ipynb](MQBI04_Lesson20_Action2_GridSearchCV_CreditCardFraud.ipynb)

---

# 19. 资金流入流出预测

---
+ push date: 2021/1/31
+ Thinking: 无
+ Action1: 资金流入流出预测
  + 主要工具：Pandas、chinese_calendar
  + 主要技术：基于时序的周期因子预测法
+ [MQBI04_Lesson19_Action1_PeriodFactor_146.7478.ipynb](./MQBI04_Lesson19_Action1_PeriodFactor_146.7478.ipynb)

+ Action2: 新闻内容自动提取及呈现
  + 主要工具：Requests、bs4、Jieba、Wordcloud、textrank4zh
  + 主要技术：爬虫、jieba分词、词云可视化、文本关键字提取（TextRank4Keyword）, 文本摘要提取（TextRank4Sentence）
  + [MQBI04_Lesson19_Action2_NewsAutomaticallyExtractedAndPresented.ipynb](./MQBI04_Lesson19_Action2_NewsAutomaticallyExtractedAndPresented.ipynb)

---


# 18. 时间序列实战

+ push date: 2021/1/24
+ Thinking: 无
+ Action1: JetRail高铁的乘客数量预测 
  + 主要工具：Pandas、Statsmodels、fbprophet、chinese_calendar
  + 主要技术：ARIMA模型、Prophet模型、ADF检验(单位根检验)、自相关图、偏自相关图
+ [MQBI04_Lesson18_Action1_prophet_jetrail_predict.ipynb](./MQBI04_Lesson18_Action1_prophet_jetrail_predict.ipynb)
+ Action2: 资金流入流出预测 
  + 主要工具：Pandas、Statsmodels、fbprophet
  + 主要技术：Prophet模型
  + [MQBI04_Lesson18_Action_fbprophet_CapitalInflowAndOutflowForecast_115_6103.ipynb](./MQBI04_Lesson18_Action_fbprophet_CapitalInflowAndOutflowForecast_115_6103.ipynb)
    [tc_comp_predict_table_fb_115_6103.csv](./tc_comp_predict_table_fb_115_6103.csv)


---
# 17. 时间序列分析

+ push date: 2021/1/3
+ Thinking: [MQBI04_Lesson17Thinking.md](./MQBI04_Lesson17Thinking.md)
+ Action1: [MQBI04_Action1_Lesson17_LSTM_PM2.5_StandardScaler.ipynb](./MQBI04_Action1_Lesson17_LSTM_PM2.5_StandardScaler.ipynb)


---
# 16. Prediction is all you Need
+ push date: 2020/12/20
+ Action1: 基于评分卡的风控模型开发
  + 主要工具：Pandas、Matplotlib、sklearn、Missingno
  + 主要技术：逻辑回归、数据分箱、WOE(Weight of Evidence)、IV(Information Value)、特征筛选
  + [MQBI04_Lesson16_Acion1_GiveMeSomeCredit_CustomBins.ipynb](./MQBI04_Lesson16_Acion1_GiveMeSomeCredit_CustomBins.ipynb)
+ Action2: 百度AI比赛：用户购买预测
+ [MQBI04_Action2_lgb_0_4956.ipynb](./MQBI04_Action2_lgb_0_4956.ipynb)




# 15. 逻辑回归与采购决策

+ push date: 2020/12/13
+ Thinking: [MQBI04_Lesson15_Thinking.md](./MQBI04_Lesson15_Thinking.md)
+ Action: kaggle 基于评分卡的风控模型开发
  + 主要工具：Pandas、Matplotlib、sklearn、Missingno
  + 主要技术：逻辑回归、数据分箱、WOE(Weight of Evidence)、IV(Information Value)、特征筛选
  + [MQBI04_Lesson15_Acion1_GiveMeSomeCredit_CustomBins.ipynb](./MQBI04_Lesson15_Acion1_GiveMeSomeCredit_CustomBins.ipynb)



---
# 14. Learning to Rank与Airbnb个性化推荐

+ push date: 2020/12/06
- Action: 天池 资金流入流出预测
	- 主要工具：Pandas、Statsmodels、fbprophet
	- 主要技术：ARIMA模型、Prophet模型、周期因子、模型融合
	- 使用周期因子预测及模型融合 [MQBI04_Lesson14_Action_PeriodicityFactor_CapitalInflowAndOutflowForecast_130_6812.ipynb](./MQBI04_Lesson14_Action_PeriodicityFactor_CapitalInflowAndOutflowForecast_130_6812.ipynb)
	- 使用fbprophet预测[MQBI04_Lesson14_Action_fbprophet_CapitalInflowAndOutflowForecast_115_6103.ipynb](./MQBI04_Lesson14_Action_fbprophet_CapitalInflowAndOutflowForecast_115_6103.ipynb)
	- 使用ARIMA预测
	- [MQBI04_Lesson14_Action_ARIMA_CapitalInflowAndOutflowForecast_100_3210.ipynb](./MQBI04_Lesson14_Action_ARIMA_CapitalInflowAndOutflowForecast_100_3210.ipynb)
	- 预测结果输出的CSV文件在文件夹[L14ModelOutputs](./L14ModelOutputs/)

---

# 13. 常见规划问题(2)

+ push date: 2020/12/02
+ Thinking: [MQBI04_Lesson13_Thinking.md](./MQBI04_Lesson13_Thinking.md)
+ Action1: Kaggle Santa的接待安排
  + 主要工具：Numpy、Pandas、Matplotlib、Ortools
  + 主要技术：线性规划LP、混合整数规划MP
  + [MQBI04_Lesoon13_Action1_Santa2019ILP-72964.ipynb](MQBI04_Lesoon13_Action1_Santa2019ILP-72964.ipynb)
+ Action2:VRP多辆车路径规划问题
  + 主要工具：Pandas、Ortools
  + 主要技术：多辆车的路径规划 VRP
  + [MQBI04_Lesson13_Action2_VRP.ipynb](./MQBI04_Lesson13_Action2_VRP.ipynb)

---
# 12. 常见规划问题(课件标题)

+ push date: 2020/11/25

+ Thinking: [MQBI04_Lesson12Thinking.md](./MQBI04_Lesson12Thinking.md)

+ Action1:Santa的接待安排
	
	+ 主要工具：Numpy、Pandas、Matplotlib、Ortools
	+ 主要技术：线性规划LP、混合整数规划MP
	
	+ [MQBI04_Lesoon12_Action1_Santa2019ILP-72964.ipynb](./MQBI04_Lesoon12_Action1_Santa2019ILP-72964.ipynb)

---
# 11.  智能供应链(二)

+ push date: 2020/11/13
+ Thinking: [MQBI04_Lesson11_Thinking.md](./MQBI04_Lesson11_Thinking.md)
+ Action1: 智能供应链分析
  + 主要工具：Pandas、Seaborn、Sklearn、XGBoost、Lightgbm
	+ 主要技术：逻辑回归、SVC(支持向量机)、GridSearchCV(参数调优)、Lasso回归、岭回归、模型融合
	+ 对于欺诈订单进行预测，即Order Status='SUSPECTED_FRAUD'[MQBI04_Lesson11_Action01_FraudPredict_DeepFM.ipynb](./MQBI04_Lesson11_Action01_FraudPredict_DeepFM.ipynb)
	+ 对于迟交货订单进行预测，即Delivery Status= 'Late delivery'[MQBI04_Lesson11_Action01_LateDelivery_DeepFM.ipynb](./MQBI04_Lesson11_Action01_LateDelivery_DeepFM.ipynb)
	+ 对于销售额进行预测，即Sales字段[MQBI04_Lesson11_Action01_SalesPredict_DeepFM.ipynb](./MQBI04_Lesson11_Action01_SalesPredict_DeepFM.ipynb)
	+ 对于订货数量进行预测，即Order Item Quantity[MQBI04_Lesson11_Action01_OrderItemQuantity_DeepFM.ipynb](./MQBI04_Lesson11_Action01_OrderItemQuantity_DeepFM.ipynb)
+ Action2: 种植不同农产品的总收益最大化问题：
  + 主要工具：Pandas、Pulp
  + 主要技术：整数线性规划(ILP)
  + [MQBI04_Lesson11_Action2_MaximizingFarmersIncomeBy_Puly.ipynb](./MQBI04_Lesson11_Action2_MaximizingFarmersIncomeBy_Puly.ipynb)

---

## 10. 智能供应链

+ push date: 2020/11/8

+ Thinking: 无

+ Action1: 智能供应链分析
  
	+ 主要工具：Pandas、Seaborn、Sklearn、XGBoost、Lightgbm
	+ 主要技术：逻辑回归、SVC(支持向量机)、GridSearchCV(参数调优)、Lasso回归、岭回归、模型融合
	
	+ 对于欺诈订单进行预测，即Order Status='SUSPECTED_FRAUD'[MQBI04_Lesson10_Action01_SUSPECTED_FRAUD_Predict.ipynb](./MQBI04_Lesson10_Action01_SUSPECTED_FRAUD_Predict.ipynb)
	+ 对于迟交货订单进行预测，即Delivery Status= 'Late delivery'[MQBI04_Lesson10_Action01_DelayShippingPredict.ipynb](./MQBI04_Lesson10_Action01_DelayShippingPredict.ipynb)
	+ 对于销售额进行预测，即Sales字段[MQBI04_Lesson10_Action01_SalesPredict.ipynb](./MQBI04_Lesson10_Action01_SalesPredict.ipynb)
	+ 对于订货数量进行预测，即Order Item Quantity[MQBI04_Lesson10_Action01_OrderItemQuantityPredict.ipynb](./MQBI04_Lesson10_Action01_OrderItemQuantityPredict.ipynb)


---

# 9. 模型融合与智能预测

+ push date: 2020/11/1
+ Thinking: 无
+ Action1: 天池 二手车价格预测
  + 主要工具：Pandas、Pytorch、Seaborn、Sklearn
  + 主要技术：DNN、早停法
  + [MQBI04_Lesson09Action1_SecondHandCarsPredict_score_474.ipynb](./MQBI04_Lesson09Action1_SecondHandCarsPredict_score_474.ipynb)
  + 预测结果:[sample_submit_SHCPredict474.csv](./sample_submit_SHCPredict474.csv)
+ Action2: 智能供应链分析EDA
  + 主要工具：Pandas、Seaborn、Matplotlib、Plotly
  + [MQBI04_Lesson09Action2_SupplyChainDatasetEDA.ipynb](./MQBI04_Lesson09Action2_SupplyChainDatasetEDA.ipynb)

---

# 8. 时间序列实战与分布式推荐系统

+ push date: 2020/10/17

+ Thinking: [MQBI04_Lesson08Thinking.md](./MQBI04_Lesson08Thinking.md)

+ Action1: JetRail高铁的乘客数量预测（交通流量预测）

  + 主要工具：Pandas、Matplotlib、Statsmodels、fbprophet、chinese_calendar
  + 主要技术：ADF检验（单位根检验）、Prophet模型

  +  [MQBI04_Lesson08Action1_dailyPassengerFlowForcastV2.ipynb](./MQBI04_Lesson08Action1_dailyPassengerFlowForcastV2.ipynb)


---

# 7. 深度卷积网络与实战

+ push date: 2020/10/17
+ Thinking: [MQBI04_Lesson07_Thinking.md](./MQBI04_Lesson07_Thinking.md)
+ Action1: 使用任何神经网络框架，对CIFAR-10数据集进行分类
  + 主要工具：Pytorch、Matplotlib
  + 主要技术：GoogleNet迁移学习、图像数据增强
  + [MQBI04_Action1_Cifar10GoogleNet_9511.ipynb](./MQBI04_Action1_Cifar10GoogleNet_9511.ipynb)
  + 保存的模型:[cifar10_googlenet_1.pt](./cifar10_googlenet_1.pt)


---

## 6. Week06: 近似最近邻查找与YouTube推荐系统

+ push date: 2020/10/02
+ Thinking: [MQBI04_Lesson06_Thinking.md](./MQBI04_Lesson06_Thinking.md)
+ Action1: 使用MinHashLSHForest对微博新闻句子进行检索 
  + 主要工具：re、Jieba、datasketch
  + 主要技术：jieba分词、MinHashForest算法、Jaccard相似度
  + [MQBI04_Lesson06_Action1_MinHashLSHForest.ipynb](./MQBI04_Lesson06_Action1_MinHashLSHForest.ipynb)

---

## 5. Week05: CTR预估算法与基于流行度的推荐

+ push date: 2020/09/25

+ Thinking: [MQBI04_Lesson05_Thinking.md](./MQBI04_Lesson05_Thinking.md)

+ Action1: 使用Wide&Deep模型对movielens进行评分预测

  + 主要工具：Pandas、Sklearn、Deepctr
  + 主要技术：Wide&Deep模型(WDL)

  +  [MQBI04_Lesson05_Action1_WideDeepRatePredict.ipynb](./MQBI04_Lesson05_Action1_WideDeepRatePredict.ipynb)

---
## 4. Week04: SVD矩阵分解与基于内容的推荐

+ push date: 2020/09/18
+ Thinking: [MQ_BI04_Lesson04_Thingking.md](./MQ_BI04_Lesson04_Thingking.md)
+ Action1: 使用SVD进行图像的重构
  + 主要工具：Numpy、Matplotlib、PIL、Scipy
  + 主要技术：图像灰度化处理、单通道及多通道图像奇异值分解(SVD)
  + [MQ_BI04_lesson04_Action01_ImageSVD.ipynb](./MQ_BI04_lesson04_Action01_ImageSVD.ipynb)
  + images: 分解前：origin_imge.jpg、分解重建：new_img.jpg
+ Action2: 对MovieLens数据集进行评分预测
  + 主要工具：Pandas、Surprise
  + 主要技术：funkSVD算法, BiasSVD算法, SVD++算法, K折交叉验证(KFold)
  + [MQ_BI04_lesson04_Action02_MovielensSVD_2.ipynb](./MQ_BI04_lesson04_Action02_MovielensSVD_2.ipynb)
+ Action3: 使用Gensim中的Word2Vec对三国演义进行Word Embedding，分析相近词
  + 主要工具：Jieba、Pandas、Gensim
  + 主要技术：Jieba分词、Word2Vec
  +  [MQ_BI04_lesson04_Action03_Word2vec.ipynb](./MQ_BI04_lesson04_Action03_Word2vec.ipynb)

---

## 3. Week03: 推荐系统眼中的你-用户画像

+ push date: 2020/9/11

+ Thinking: [MQ_BI04_Lesson03_Thingking.md](./MQ_BI04_Lesson03_Thingking.md)

+ Action1:针对Delicious数据集，对SimpleTagBased算法进行改进（使用NormTagBased、TagBased-TFIDF算法）

   + 主要工具：Numpy、Pandas
   + 主要技术：SimpleTagBased算法、NormTagBased-1和NormTagBased-2算法、TagBased-TFIDF算法

   [MQ_BI04_lesson03_Action01_delicious_recommend.ipynb](./MQ_BI04_lesson03_Action01_delicious_recommend.ipynb)

+ Action2:对Titanic数据进行清洗，建模并对乘客生存进行预测。使用之前介绍过的10种模型中的至少2种（+包括TPOT）

   + 主要工具：Pandas、Matplotlib、Seaborn、Sklearn、TPOT、XGBoost
   + 主要技术：决策树、朴素贝叶斯的3模型、KNN、逻辑回归、AdaBoost、LDA(LinearDiscriminantAnalysis)、自动机器学习TPOT
   
   [MQ_BI04_lesson03_Action02_Titanic.ipynb](./MQ_BI04_lesson03_Action02_Titanic.ipynb)

---

## 2. week02: 数据可视化及实战

+ push date: 2020/8/29

+ Thinking: [名企BI04_Lesson02_Thingking.txt](./名企BI04_Lesson02_Thingking.txt)

+ Action1:购物篮词云分析
  数据集：MarketBasket
  下载地址：https://www.kaggle.com/dragonheir/basket-optimisation
  对数据集进行词云可视化展示，可视化探索（Top10的商品有哪些）

  + 主要工具：Wordcloud、Pandas、Matplotlib、Seaborn
  + 主要技术：WordCloud，蒙版
  
   [名企BI04lesson02_Action1_购物篮可视化.ipynb](./名企BI04lesson02_Action1_购物篮可视化.ipynb)

---

## 1. week01: 数据采集与实战

+ push date: 2020/8/22

+ Thinking: [名企BI04_Lesson01_Thingking.md](./名企BI04_Lesson01_Thingking.md)

+ Action1:不用任何数学库，如何求出sqrt(10)，并且精确到小数点后10位

   [名企BI04Lesson01_Action1_10开平方.ipynb](./名企BI04Lesson01_Action1_10开平方.ipynb)

+ Action2: 汽车投诉信息采集：
  数据源：http://www.12365auto.com/zlts/0-0-0-0-0-0_0-0-1.shtml
  投诉编号，投诉品牌，投诉车系，投诉车型，问题简述，典型问题，投诉时间，投诉状态
  可以采用Python爬虫，或者第三方可视化工具

  + 主要工具：re、Requests、Pandas、BeautifulSoup
  + 主要技术：爬取静态html，爬取.js数据

  [名企BI04Lesson01_Action2_汽车投诉信息采集.ipynb](./名企BI04Lesson01_Action2_汽车投诉信息采集.ipynb)

