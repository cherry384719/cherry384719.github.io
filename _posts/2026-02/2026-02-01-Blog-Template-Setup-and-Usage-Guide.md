---
title: Blog Template Setup and Usage Guide
description: 根据官方及huanyushi大佬的教程，对Chirpy主题相关使用方法进行总结
date: 2026-02-01
categories: [shares]
tags: [template]

math: true
pin: true

---


## 参考
- [**chirpy官方文档**](https://chirpy.cotes.page/posts/write-a-new-post/)

- [**huanyushi大佬教程**](https://huanyushi.github.io/posts/chirpy-blog-customization/)


## 1.设置**`Front Matter`**

```markdown
---
title: TITLE
description: Optional (default: empty)
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [TOP_CATEGORY, SUB_CATEGORY]
tags: [TAG]     # TAG names should always be lowercase

image:
  path: /path/to/image
  alt: image alternative text

math: Optional (default: false)
mermaid: Optional (default: false)
media_subpath: /path/to/media/
pin: true  # pin one or more posts to the top of the home page
toc: Optional (default: true)   # the Table of Contents
comments: Optional (default: true)

---
```

## 2.常用语法：

### 2.1 Prompt

#### 模板作者已经设置的4个prompt
```markdown
> Example line for prompt.
{: .prompt-info }
```
还有`{: .prompt-tip}`、`{: .prompt-warning}`、`{: .prompt-danger}`，
下面是info显示效果：
> Example line for prompt.
{: .prompt-info }

#### 大佬添加的新prompt
```markdown
<div class="box-tip" markdown="1">
<div class="title"> Shakespeare </div>
To be or not to be. That is a question.
</div>
```
可将其中的`box-tip`换为其他三个：`box-info`、`box-warning`、`box-danger`，下面是tip显示效果：

<div class="box-tip" markdown="1">
<div class="title"> Shakespeare </div>
To be or not to be. That is a question.
</div>

也可以不加标题，即去掉`<div class="title"> Shakespeare </div>`，效果：

<div class="box-tip" markdown="1">
To be or not to be. That is a question.
</div>

### 2.2 Details 元素

#### 2.2.1 details-block
HTML 中的 `<details class="details-block">` 元素可以创建一个组件，仅当被切换为展开状态时，才会显示里面的内容，效果如下：

<details class="details-block" markdown="1">
<summary>详细信息 </summary>
床前明月光，疑是地上霜。举头望明月，低头思故乡。

$$
x^2 + y^2 =z^2, \quad x_{1,2} = \frac{-b\pm\sqrt{b^2-4ac}}{2a}
$$

</details>

在 Markdown 文件输入以下代码即可实现，其中 `markdown = "1"` 是为了在 HTML 元素内也可以使用 Markdown 语法，另外在其中加入 open 可以设置它为默认展开的形式（否则为默认关闭）：
```markdown
<details class="details-block" markdown="1">
<summary>详细信息</summary>
床前明月光，疑是地上霜。举头望明月，低头思故乡。

$$
x^2 + y^2 =z^2, \quad x_{1,2} = \frac{-b\pm\sqrt{b^2-4ac}}{2a}
$$

</details>
```

#### 2.2.2 details-inline
更简洁的一种details显示方式（截取自[huanyushi大佬的文章](https://huanyushi.github.io/posts/topological-manifolds-exercise/)）：

<details class="details-inline" markdown="1">
<summary>Proof</summary>
**(d):** 对于任意给定集合 $X$ ，定义离散度量 $d:X\times X\to \mathbb{R}$ 为：

$$
\begin{equation*}
    d(x,y) = \begin{cases}
        0, \quad &\text{if $x=y$}\\[.2cm]
        1, & \text{if $x\neq y$}
    \end{cases}
\end{equation*}
$$

对于任意 $x\in X$，不妨取 $r=1/2$，依据离散度量的上述定义，我们可以知道 $B_{r}^{(d)}(x) = \set{x}$。因此所有单点集 $\set{x}$ 都是开集。

对于任意子集 $A \subseteq X$，我们可以把它写为 $A = \bigcup_{x\in A}\set{x}$。由于拓扑中的开集闭合于任意并，且每个 $\set{x}$ 是开集，所以 $A$ 也是开集。

于是 $X$ 的所有子集都是开集，由离散度量 $d$ 生成的拓扑正是幂集 $\mathcal{P}(x)$，即离散拓扑。 <span style="float: right;">&#x220E;</span>

**(e):** 我们只需证明以下两点：

- 离散度量 $d$ 生成的每个开集，在欧式度量下也是开集；
- 欧式度量 $d'$ 生成的每个开集，在离散度量下也是开集。

考虑任意 $x\in\mathbb{Z}$，在 (d) 中我们已经证明了离散度量下 $\set{x}$ 是开集。在欧式度量下，同样取 $r=1/2$，我们有 $B_{r}^{(d')}(x) =\set{x}$，所以单点集 $\set{x}$ 也是开集。

考虑到 $\mathbb{Z}$ 的任意子集都可以写成单点集 $\set{x}$ 的并，所以在两个度量生成的拓扑中都属于开集。于是它们在 $\mathbb{Z}$ 上生成同一个拓扑（也是离散拓扑）。 <span style="float: right;">&#x220E;</span>

</details>

语法：
```markdown
<details class="details-inline" markdown="1">
<summary>title</summary>

Latex & markdown

</details>
```

### 2.3 图片

#### 2.3.1 显示设置
对于基本的md语法来说，图片显示方法为：`![descriptiom](path/to/image)`。此外，在本主题中还能对图片大小、位置、名称、阴影进行调整。

```markdown
![img-description](/path/to/image)
_Image Caption_   // 图片名称

// 调节图片大小，一般只调 w 的值就行，h 会自适应
![Desktop View](/assets/img/sample/mockup.png){: w="700" h="400" }

// 相对位置的调节，此时无法对图像进行命名
![descriptiom](path/to/image){: .normal}   // 默认居中
![descriptiom](path/to/image){: .left}     // 左
![descriptiom](path/to/image){: .right}    // 右

![Desktop View](/assets/img/sample/mockup.png){: .shadow } // 阴影效果
```

对于亮暗主题，可设置显示不同的图片：
```markdown
![Light mode only](/path/to/light-mode.png){: .light }
![Dark mode only](/path/to/dark-mode.png){: .dark }
```

#### 2.3.2 存放规范
封面图片放在`~/assets/img`中，其他图片建议放在图床上。

<div class="box-tip" markdown="1">
<div class="title"> 好用的图床项目 </div>
- [Telegraph-Image](https://github.com/cf-pages/Telegraph-Image) （正在使用中）
- [PicX](https://picx.xpoet.cn/#/) 
- [PicGo](https://github.com/Molunerfinn/PicGo)
</div>

个人图床网址：[https://photo.20061204.xyz/](https://photo.20061204.xyz/)


## 3.文件规范操作

### 3.1 命名
在`_posts`文件夹中添加的markdown文件应命名为`YYYY-MM-DD-your-title.md`。

### 3.2 代码、pdf文件和数据集等
不应放在根目录下，建议新建仓库存放，链接到github上。[本博客代码仓库](https://github.com/cherry384719/Code_storage)。

对于Jupyter Notebook文件，还可以通过[https://nbviewer.org/](https://nbviewer.org/)这个网站进行链接预览。

> 代码块中的缩进要用**空格**而不是**制表符**，否则渲染出的代码缩进会过大。
{: .prompt-info}