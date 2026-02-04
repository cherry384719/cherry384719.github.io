---
title: Boston Housing Price Forecast
description: 波士顿房价预测--多元线性回归模型
date: 2026-02-04 22:00:00 +0800
categories: [machine learning]
tags: [regression]     # TAG names should always be lowercase

---

- [**Boston-Housing-Price-Forecast.ipynb**](https://github.com/cherry384719/Code_storage/blob/main/Boston-Housing-Price-Forecast.ipynb)

**利用正则化线性回归和随机梯度下降线性回归进行预测，损失函数选择均方误差MSE。**

## 1. 导包、加载数据集

> 由于某些原因，无法在sklearn.datasets中得到数据，需按提示加载数据。
{: .prompt-info}

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression    # 正则化线性回归
from sklearn.linear_model import SGDRegressor        # 随机梯度下降线性回归
from sklearn.metrics import mean_squared_error       # 均方误差
from sklearn.preprocessing import StandardScaler

# 1. 加载波士顿房价数据集
data_url = "http://lib.stat.cmu.edu/datasets/boston"
raw_df = pd.read_csv(data_url, sep="\\s+", skiprows=22, header=None)
data = np.hstack([raw_df.values[::2, :], raw_df.values[1::2, :2]])
target = raw_df.values[1::2, 2]
```

## 2. 数据预处理及特征缩放

```python
# 2. 预处理
X_train, X_test, y_train, y_test = train_test_split(data, target, test_size=0.2, random_state=42)

# 3. 特征缩放
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

## 3. 模型训练、预测和评估

```python
# 4. 训练模型
# 线性回归模型
lin_reg = LinearRegression()
lin_reg.fit(X_train, y_train)

# 随机梯度下降线性回归模型
sgd_reg = SGDRegressor(max_iter=1000, tol=1e-3)
sgd_reg.fit(X_train, y_train)

# 5. 模型预测
y_pred_lin = lin_reg.predict(X_test)
y_pred_sgd = sgd_reg.predict(X_test)

# 6. 评估模型
mse_lin = mean_squared_error(y_test, y_pred_lin)
mse_sgd = mean_squared_error(y_test, y_pred_sgd)
print(f"线性回归模型均方误差: {mse_lin:.2f}")
print(f"随机梯度下降线性回归模型均方误差: {mse_sgd:.2f}")
```

## 4. 可视化
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(10, 6))
plt.subplot(2, 1, 1)
plt.plot(y_test, label='True Values', marker='o')
plt.plot(y_pred_lin, label='Linear Regression Predictions', marker='x')
plt.xlabel('Sample Index')
plt.ylabel('House Price')
plt.title('Linear Regression Predictions')
plt.legend()

plt.subplot(2, 1, 2)
plt.plot(y_test, label='True Values', marker='o')
plt.plot(y_pred_sgd, label='SGD Regression Predictions', marker='s')
plt.xlabel('Sample Index')
plt.ylabel('House Price')
plt.title('SGD Regression Predictions')
plt.legend()

plt.tight_layout()
plt.show()
```

![可视化结果](https://blog.20061204.xyz/PicGo/output.png)