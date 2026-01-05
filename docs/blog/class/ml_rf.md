---
title: 随机森林
---

# Random Forest

- 核心思想：群体智慧
- 归属：[[集成学习]]中的Bagging（类并行）
- 优点： 准确率高，抗过拟合强，对数据要求友好
- 缺点： 计算成本高，可解释性差，预测速度慢

## 过程

- 数据采集：有放回的随机抽样（bootstrap采样），生成多个子数据集
- 构建决策树：每次分裂只考虑部分随即特征（通常是总特征数的开方）
- 训练决策树
- 聚合预测：分类投票，回归平均
- 输出


## 重要参数

- n_estimators：树的数量（计算量）
- max_depth：最大树深（控制复杂度）
- min_samples_split：分裂内部节点所需最小样本数
- min_samples_leaf：叶节点最少样本数
- max_features：寻找最佳分裂时考虑的特征数
- bootstrap：是否使用bootstrap抽样
- criterion：分裂标准（gini/entropy）
- random_state：随机种子
- n_jobs：并行运行的核心数
- oob_score：是否使用袋外样本评估

## 代码

	  import numpy as np
	  import pandas as pd
	  from sklearn.ensemble import RandomForestClassifier #分类
	  from sklearn.ensemble import RandomForestRegressor  #回归
	  