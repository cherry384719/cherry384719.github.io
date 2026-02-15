---
title: Multiple linear regression
description: 多元线性回归数学基础
date: 2026-02-04
categories: [machine learning]
tags: [regression]     # TAG names should always be lowercase

image: https://blog.20061204.xyz/PicGo/2026/02/29a5436030999cf9a9691e8f8e2eec91.png

math: true
---


## 1. 模型定义

对于有 $n$ 个特征的多元线性回归：

$$h_\theta(x) = \theta_0 + \theta_1 x_1 + \theta_2 x_2 + \cdots + \theta_n x_n$$

## 2. 向量化形式

引入偏置项 $x_0 = 1$，模型可写成：

$$h_\theta(x) = \theta^T x = \sum_{j=0}^{n} \theta_j x_j$$

其中：
- $x = \begin{bmatrix} x_0 \\ x_1 \\ \vdots \\ x_n \end{bmatrix} = \begin{bmatrix} 1 \\ x_1 \\ \vdots \\ x_n \end{bmatrix}$ 是特征向量（$n+1$ 维）

- $\theta = \begin{bmatrix} \theta_0 \\ \theta_1 \\ \vdots \\ \theta_n \end{bmatrix}$ 是参数向量（$n+1$ 维）

## 3. 矩阵形式

对于 $m$ 个训练样本：

$$\begin{bmatrix}
h_\theta(x^{(1)}) \\
h_\theta(x^{(2)}) \\
\vdots \\
h_\theta(x^{(m)})
\end{bmatrix} = \begin{bmatrix}
1 & x_1^{(1)} & x_2^{(1)} & \cdots & x_n^{(1)} \\
1 & x_1^{(2)} & x_2^{(2)} & \cdots & x_n^{(2)} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
1 & x_1^{(m)} & x_2^{(m)} & \cdots & x_n^{(m)}
\end{bmatrix} \begin{bmatrix}
\theta_0 \\
\theta_1 \\
\vdots \\
\theta_n
\end{bmatrix}$$

简写为：

$$\boxed{\hat{y} = X\theta}$$

其中：
- $X \in \mathbb{R}^{m \times (n+1)}$ 是设计矩阵
- $\theta \in \mathbb{R}^{n+1}$ 是参数向量
- $\hat{y} \in \mathbb{R}^{m}$ 是预测向量

## 4. 损失函数

均方误差（MSE）[^1]：

$$J(\theta) = \frac{1}{2m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2$$

向量形式：

$$J(\theta) = \frac{1}{2m} ||X\theta - y||^2 = \frac{1}{2m} (X\theta - y)^T(X\theta - y)$$

## 5. 参数求解方法

### 5.1 正规方程法

$$\theta = (X^T X)^{-1} X^T y$$

<details class="details-inline" markdown="1">
<summary>证明</summary>

**令损失函数梯度为0，可求得上述 $$\theta$$ 结果。只需证明该函数的极值就是最值，即为凸函数。**

#### 损失函数的凸性证明（Hessian 矩阵法）

多元线性回归的损失函数为：

$$
J(\theta)=\frac{1}{2m}(X\theta-y)^T(X\theta-y)
$$

首先对 $\theta$ 求梯度：

$$
\nabla_\theta J(\theta)
= \frac{1}{m}(X^TX\theta - X^Ty)
$$

再对梯度求导，得到 Hessian 矩阵：

$$
\nabla^2_\theta J(\theta)
= \frac{1}{m}X^TX
$$

下面证明该 Hessian 矩阵是半正定的。

对任意向量 $z \in \mathbb{R}^{n+1}$，有：

$$
z^T \nabla^2 J(\theta) z
= \frac{1}{m} z^T X^T X z
= \frac{1}{m} (Xz)^T (Xz)
= \frac{1}{m}\|Xz\|^2 \ge 0
$$

因此：

$$
\nabla^2 J(\theta) \succeq 0
$$

即损失函数 $J(\theta)$ 为凸函数。

当 $X^TX$ 为正定矩阵（即特征矩阵 $X$ 列满秩）时，  
$J(\theta)$ 为严格凸函数，其最优解唯一。

由于凸函数的任一驻点都是全局最小点，因此只需求解：

$$
\nabla_\theta J(\theta)=0
$$

即可得到全局最优解。



</details>


### 5.2 梯度下降法

$$\nabla J(\theta) = \frac{1}{m} X^T(X\theta - y)$$

**更新规则**：

$$\theta := \theta - \alpha \nabla J(\theta) = \theta - \frac{\alpha}{m} X^T(X\theta - y)$$

<details class="details-inline" markdown="1">
<summary>代码实现</summary>

```python
# 求当前theta点的梯度
def compute_gradient(X, y, theta):
    m = len(y)
    return (1 / m) * X.T @ (X @ theta - y)

def gradient_descent(X, y, lr=0.1, epochs=1000):
    n = X.shape[1]
    theta = np.zeros(n)

    for _ in range(epochs): # 一步步沿梯度下降方向前进
        grad = compute_gradient(X, y, theta)
        theta -= lr * grad

    return theta
```

</details>



### 5.3 综合对比表

| 特性 | 正规方程法 | 梯度下降法 |
|------|-----------|-----------|
| **时间复杂度** | $O(n^3)$ | $O(kmn)$，$k$ 为迭代次数 |
| **学习率** | 不需要 | 需要调整 |
| **迭代** | 不需要 | 需要多次迭代 |
| **特征缩放** | 不需要 | 需要（加快收敛） |
| **大规模特征** | 慢（$n > 10,000$） | 快 |
| **可扩展性** | 仅适用于线性回归 | 适用于各种模型 |
| **内存需求** | 需要存储 $X^T X$ | 可使用mini-batch |
| **数值稳定性** | 可能出现 $X^T X$ 不可逆 | 较稳定 |

### 5.4 选择建议

**使用正规方程法**：
- 特征数量较少（$n \leq 10,000$）
- 需要精确解
- 数据量不是特别大，可以一次性加载到内存
- $X^T X$ 可逆

**使用梯度下降法**：
- 特征数量很多（$n > 10,000$）
- 数据量很大
- 需要在线学习或增量学习
- 后续可能扩展到非线性模型
- 可以接受近似解

**使用正则化正规方程**（当 $X^T X$ 不可逆时）：

$$\theta = (X^T X + \lambda I)^{-1} X^T y$$

其中 $\lambda > 0$ 保证矩阵可逆并防止过拟合。



[^1]: [均方误差](https://zh.wikipedia.org/wiki/%E5%9D%87%E6%96%B9%E8%AF%AF%E5%B7%AE)(MSE)、[均方根误差](https://zh.wikipedia.org/wiki/%E5%9D%87%E6%96%B9%E6%A0%B9%E8%AF%AF%E5%B7%AE)(RMSE)对于离群值敏感，[平均绝对误差](https://zh.wikipedia.org/wiki/%E5%B9%B3%E5%9D%87%E7%BB%9D%E5%AF%B9%E8%AF%AF%E5%B7%AE)(MAE)怕整体偏差。训练时一般用MSE，好优化。MSE 用来“学”，RMSE 用来“看”，MAE 用来“抗异常”。
