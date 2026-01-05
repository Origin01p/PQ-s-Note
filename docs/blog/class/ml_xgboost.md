---
title: XGboost
---

## 简介

XGboost（eXtreme Gradient Boosting）直译极度梯度提升。

- 归属：集成学习—Boosting—梯度提升决策树（GBDT）—XGBoost
- 优点：简单高效可扩展，可自动处理缺失值。
- 缺点：在大数据处理环节，精度不如深度学习

## 进步和提升（相比GBDT）

- 采用二阶泰勒展开：优化损失函数，使得梯度下降更精准，收敛更快。
- 正则化：有效防止过拟合
- 支持并行计算：特征选择，Blocks存储。

## 重要参数

- eta：学习率，默认0.3
- booster：基学习器类型，常见有"gbtree"（树模型），"gblinear"（线性模型）,"dart"（带Dropout树）
- min_child_weight： 叶子节点样本权重和的最小值
- max_depth：树的最大深度
- n_estimators：树的数量
- subsample：每棵树使用的样本比例（行采样）
- colsample_bytree：每棵树使用的特征比例（列采样）
- gamma：最小分裂增益
- alpha/lambda：L1，L2正则化系数
- objective：定义任务类型（如二分类、多分类、回归）



## 数学表达式

目标函数：

$$
\text{Obj}(\theta) = \sum_{i=1}^{n} L(y_i, \hat{y}_i) + \sum_{k=1}^{K} \Omega(f_k)
$$

前者为损失项（预测值与真实值的差），后者为正则化项（L2，L1，衡量模型复杂度）：
$$
\Omega(f) = \gamma T + \frac{1}{2} \lambda \|w\|^2 + \alpha \|w\|_1
$$

泰勒展开（二阶）近似：

$$
\begin{aligned}
\text{Obj}^{(t)} &= \sum_{i=1}^{n} L(y_i, \hat{y}_i^{(t-1)} + f_t(x_i)) + \Omega(f_t) \\
&\approx \sum_{i=1}^{n} \left[ L(y_i, \hat{y}_i^{(t-1)}) + g_i f_t(x_i) + \frac{1}{2} h_i f_t^2(x_i) \right] + \Omega(f_t)
\end{aligned}
$$



## 代码

	 from xgboost import XGBClassifier
	 from sklearn.model_selection import train_test_split
	 
	 model = XGBClassifier(
		 n_estimators = 100, 
		 max_depth = 3,
		 learning_rate = 0.1
	)
	
	 model.fit(X_train, Y_train)
	 y_pred = model.predict(X_test)