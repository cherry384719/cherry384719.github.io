---
title: Three cases of fitting
description: 线性回归中的三种拟合情况分析
date: 2026-02-05
categories: [machine learning]
tags: [fitting]     # TAG names should always be lowercase

math: true

image: https://blog.20061204.xyz/PicGo/2026/02/c94b2630f3941cb7801be1df3cff5c82.png
---

> 代码文件：
[**Three_cases_of_fitting.ipynb**](https://github.com/cherry384719/Code_storage/blob/main/Three_cases_of_fitting.ipynb)
{: .prompt-info}


## 拟合的三种情况：欠拟合、恰当拟合、过拟合

**核心概念**：机器学习模型的复杂度应该与数据的真实规律相匹配。

### 实验设置

- **真实数据关系**：$y = 0.5x^2 + x + 2 + \text{噪声}$（二次函数）
- **数据量**：100个样本
- **目标**：通过调整特征数量，演示三种拟合状态

---

### 1. 特征不足：欠拟合（Underfitting）

**问题**：使用线性回归（1个特征）拟合二次函数数据
- 模型复杂度 < 数据复杂度
- 无法捕捉数据的非线性规律
- 导致高偏差（High Bias）

#### 代码实现

```python
# 欠拟合 - 特征太少
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

# 生成数据：真实关系为 y = 0.5*x² + x + 2 + 噪声
np.random.seed(0)
x = 2 * np.random.uniform(-3, 3, size=100)
y = 0.5 * x**2 + x + 2 + np.random.normal(0, 2, size=100)

# 预处理：转为列向量 (100, 1)
X = x.reshape(-1, 1)

# 拟合线性模型：ŷ = a₁*x + b（只能学习直线）
model = LinearRegression()
model.fit(X, y)
y_pred = model.predict(X)

# 显示学到的系数
print(f"欠拟合模型：y = {model.coef_[0]:.3f}*x + {model.intercept_:.3f}")
print(f"真实公式：y = 1.000*x + 0.500*x² + 2.000 (+ noise)")
print(f"训练MSE: {np.mean((y_pred - y)**2):.3f}")
print()

# 可视化
plt.figure(figsize=(8, 5))
plt.scatter(x, y, color='blue', alpha=0.6, label='Real Data')
plt.plot(np.sort(x), model.predict(np.sort(x).reshape(-1, 1)), 
         color='red', linewidth=2, label='Linear Fit (Underfitting)')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Case 1: Underfitting - Model too simple')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()
```

<details class="details-inline" markdown="1">
<summary>运行结果</summary>

欠拟合模型：y = 0.782*x + 8.351

真实公式：y = 1.000*x + 0.500*x² + 2.000 (+ noise)

训练MSE: 30.917

![Underfitting](https://blog.20061204.xyz/PicGo/2026/02/c3d974c81c0e688984f3070d256e80ec.png){: .normal}

</details>


---

### 2. 特征合适：恰当拟合（Good Fit）

**方案**：添加二次项特征 $x^2$，构建多项式回归
- 模型形式：$\hat{y} = a_1 \cdot x + a_2 \cdot x^2 + b$
- 模型复杂度 ≈ 数据复杂度
- 模型能够充分学习数据规律
- 在训练集和测试集上表现均衡（Low Bias, Low Variance）

#### 代码实现

```python
# 恰当拟合 - 添加二次项特征
# 构建特征矩阵：X2 = [x, x²]，形状为 (100, 2)
X2 = np.column_stack((X, X**2))

# 拟合模型：ŷ = a₁*x + a₂*x² + b
model2 = LinearRegression()
model2.fit(X2, y)
y_pred2 = model2.predict(X2)

# 显示学到的系数
print(f"恰当拟合模型：y = {model2.coef_[0]:.3f}*x + {model2.coef_[1]:.3f}*x² + {model2.intercept_:.3f}")
print(f"真实公式：  y = 1.000*x + 0.500*x² + 2.000 (+ noise)")
print(f"训练MSE: {np.mean((y_pred2 - y)**2):.3f}")
print()

# 可视化
plt.figure(figsize=(8, 5))
plt.scatter(x, y, color='blue', alpha=0.6, label='Real Data')
# 按x排序后绘制平滑曲线
sorted_idx = np.argsort(x)
x_sorted = x[sorted_idx]
X2_sorted = X2[sorted_idx]
y_pred2_sorted = model2.predict(X2_sorted)
plt.plot(x_sorted, y_pred2_sorted, color='red', linewidth=2, label='Polynomial Fit (Good Fit)')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Case 2: Good Fit - Model complexity matches data')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()
```

<details class="details-inline" markdown="1">
<summary>运行结果</summary>

恰当拟合模型：y = 0.979*x + 0.475*x² + 2.681

真实公式：  y = 1.000*x + 0.500*x² + 2.000 (+ noise)

训练MSE: 3.894

![Goodfitting](https://blog.20061204.xyz/PicGo/2026/02/5404504e533bac77f3b627b9023ec02d.png){: .normal}

</details>

---

### 3. 特征过多：过拟合（Overfitting）

**问题**：添加14次多项式特征 $(x, x^2, ..., x^{14})$
- 模型复杂度 >> 数据复杂度
- 模型不仅学习数据规律，还拟合了噪声
- 在训练集上表现好，但泛化能力差（Low Bias, High Variance）
- 曲线呈现过度波动

#### 代码实现

```python
# 过拟合 - 特征太多
# 构建14次多项式特征矩阵：X_high = [x, x², x³, ..., x¹⁴]，形状为 (100, 14)
X_high = np.column_stack([X**i for i in range(1, 15)])

# 拟合高阶多项式模型
model_high = LinearRegression()
model_high.fit(X_high, y)
y_pred_high = model_high.predict(X_high)

# 显示模型性能
print(f"过拟合模型：14次多项式")
print(f"训练MSE: {np.mean((y_pred_high - y)**2):.3f}")
print(f"模型参数数量: 14 + 1(截距) = 15个")
print(f"数据样本数: 100个")
print(f"参数/样本比: {15/100:.2%}")
print()

# 可视化
plt.figure(figsize=(8, 5))
plt.scatter(x, y, color='blue', alpha=0.6, label='Real Data')
# 按x排序后绘制曲线
sorted_idx = np.argsort(x)
x_sorted = x[sorted_idx]
X_high_sorted = X_high[sorted_idx]
y_pred_high_sorted = model_high.predict(X_high_sorted)
plt.plot(x_sorted, y_pred_high_sorted, color='red', linewidth=2, label='14th Degree Polynomial (Overfitting)')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Case 3: Overfitting - Model fits noise, not just pattern')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()
```

<details class="details-inline" markdown="1">
<summary>运行结果</summary>

过拟合模型：14次多项式

训练MSE: 3.632

模型参数数量: 14 + 1(截距) = 15个

数据样本数: 100个

参数/样本比: 15.00%


![Overfitting](https://blog.20061204.xyz/PicGo/2026/02/06c1e907afe7c765d256656a602ede4d.png){: .normal}

</details>

---

### 总结对比

| 指标 | 欠拟合 | 恰当拟合 | 过拟合 |
|------|--------|---------|--------|
| **特征数量** | 1个 (x) | 2个 (x, x²) | 14个 (x, ..., x¹⁴) |
| **模型复杂度** | 低 | 中 | 高 |
| **训练误差** | 高 | 低 | 最低 |
| **测试误差** | 高 | 低 | 高 |
| **偏差** | 高 | 低 | 低 |
| **方差** | 低 | 低 | 高 |
| **可视化** | 欠拟合直线 | 贴近数据曲线 | 过度波动 |
| **学习情况** | 未学到数据规律 | ✓ 学到了二次关系 | 学到了噪声 |

#### 核心要点

1. **欠拟合原因**：特征不足，模型学习能力受限
   - 解决方案：增加相关特征

2. **恰当拟合的目标**：特征数量与数据复杂度匹配
   - 模型在训练集和新数据上表现都好
   - 这是机器学习的理想状态

3. **过拟合原因**：特征过多，模型学到了训练数据中的噪声
   - 解决方案：
     - 减少特征数量
     - 使用正则化 (L1/L2)
     - 增加训练数据
     - 提前停止
