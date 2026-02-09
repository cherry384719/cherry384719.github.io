---
title: Regularization L1/L2
description: L1/L2 正则化
date: 2026-02-09
categories: [machine learning]
tags: [regularization]     # TAG names should always be lowercase

math: true

---

## 使用正则化 (L1/L2)解决过拟合问题

### 介绍

详细内容见[参考博客](https://www.cnblogs.com/zingp/p/10375691.html)

<div class="box-info" markdown="1">
<div class="title"> 摘记 </div>

L1正则化和L2正则化可以看做是**损失函数的惩罚项**。所谓**惩罚**是指对损失函数中的**某些参数做一些限制**。对于线性回归模型，**使用L1正则化的模型叫做Lasso回归，使用L2正则化的模型叫做Ridge回归（岭回归）**。


线性回归L1正则化损失函数：

$$\min_{\mathbf{w}} \sum_{i=1}^{N} \left( \mathbf{w}^T \mathbf{x}_i - y_i \right)^2+ \lambda \lVert \mathbf{w} \rVert_1$$


线性回归L2正则化损失函数：

$$\min_{\mathbf{w}} \sum_{i=1}^{N} \left( \mathbf{w}^T \mathbf{x}_i - y_i \right)^2+ \lambda \lVert \mathbf{w} \rVert_2^2$$

二者都是基于惩罚系数$\alpha$ 来修改特征列的权重，系数越大，则修改力度越大，对应权重就越小。

区别：

-   L1 正则化可能让权重变0，选择后得到稀疏的特征
-   L2 正则化只能让权重无限趋于0，但是不能为0，选择后的特征不具有稀疏性

</div>



### 代码实现

参考之前的三种线性拟合的代码，只需将模型选为`Lasso` 或 `Ridge` 即可

```python
# 从sklearn.linear_model导入Lasso(L1正则化)和Ridge(L2正则化)
from sklearn.linear_model import Lasso, Ridge

# 将模型换为Lasso 和 Ridge 进行训练
model_lasso = Lasso(alpha=0.1) # alpha为正则化参数(惩罚系数)
model_ridge = Ridge(alpha=0.1)
model_lasso.fit(X_high, y)
model_ridge.fit(X_high, y)
y_pred_lasso = model_lasso.predict(X_high)
y_pred_ridge = model_ridge.predict(X_high)
# 显示模型性能
print(f"Lasso (L1) 正则化模型训练MSE: {np.mean((y_pred_lasso - y)**2):.3f}")
print(f"Ridge (L2) 正则化模型训练MSE: {np.mean((y_pred_ridge - y)**2):.3f}")
print()

# 可视化
...
```

运行结果：
> Lasso (L1) 正则化模型训练MSE: 3.875
>
> Ridge (L2) 正则化模型训练MSE: 3.632
>
>![img](https://blog.20061204.xyz/PicGo/2026/02/a8a6ea47e62225a7707cc9fe7872e4d5.png){: w="600" .normal}

过拟合原图：

![img](https://blog.20061204.xyz/PicGo/2026/02/06c1e907afe7c765d256656a602ede4d.png){: w="600" .normal}

**可以看到使用正则化拟合的效果变好了一些。**

## 参考
> 一篇讲解得很详细的[博客](https://www.cnblogs.com/zingp/p/10375691.html) 
{: .prompt-tip}