---
title: Blog Template Setup and Usage Guide
description: 根据官方及huanyushi大佬的教程，对Chirpy主题相关使用方法进行总结。本博客主题参考自huanyushi大佬的配置。
date: 2026-02-01
categories: [template]
tags: [blog]

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

## 2. Prompt

### 模板作者已经设置的4个prompt
```markdown
> Example line for prompt.
{: .prompt-info }
```
还有`{: .prompt-tip}`、`{: .prompt-warning}`、`{: .prompt-danger}`，
下面是info显示效果：
> Example line for prompt.
{: .prompt-info }

### 大佬添加的新prompt
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

## 3. Details 元素

### 3.1 details-block
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

### 3.2 details-inline
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

## 4. 图片

### 显示设置
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

### 存放规范
图片建议放在自建图床上，推荐使用 Cloudflare R2 / GitHub + PicGo组合。

<div class="box-tip" markdown="1">
<div class="title"> 好用的图床项目 </div>
- [**Telegraph-Image**](https://github.com/cf-pages/Telegraph-Image)  （基于telegram的图片接口）
- [**PicX**](https://picx.xpoet.cn/#/) （基于github pages）
- [**PicGo + Cloudflare R2**](https://github.com/Molunerfinn/PicGo) （桌面软件，为通用图床上传工具，需配置接口）
</div>

个人图床网址：
1. [https://photo.20061204.xyz/](https://photo.20061204.xyz/) （Telegraph-Image）
2. [https://blog.20061204.xyz/{fileName}](https://blog.20061204.xyz/) （Cloudflare R2 + PicGo）

## 5. PDF文件、PPT等
推荐存放于Cloudflare R2中（能在浏览器中直接进行预览），markdown展示语法：

1.**直接跳转**

```markdown
[📄 查看 PDF](https://你的R2域名/xxx.pdf)
```

2.**iframe 内嵌预览**

```markdown
<iframe
  src="https://你的R2域名/xxx.pdf"
  width="100%"
  height="800px">
</iframe>
```


## 6. 视频、音频展示

可对流媒体平台视频、个人视频、音频进行展示，详细信息参考[官方文档](https://chirpy.cotes.page/posts/write-a-new-post/#social-media-platforms)。

视频展示简便方法：
```markdown
<video
  src="https://你的R2域名/demo.mp4"
  controls
  width="100%"
  preload="metadata">
</video>
```

## 7. github 贡献图

**博客中在`about`页面展示的github贡献图的两种显示方法介绍。**

### 7.1 复制即用，方便快捷

来自[github项目](https://github.com/2016rshah/githubchart-api)，只需将这一行代码
```html
<img src="https://ghchart.rshah.org/2016rshah" alt="2016rshah's Github chart" />
```
插入到markdown文档中，将其中的`2016rshah`替换为你的github名称即可显示。当然也可根据官方文档调节显示颜色。显示效果：

![img](https://blog.20061204.xyz/PicGo/2026/02/259a920eb2b60b21308c330e30f8ce64.png){: .light}

![img](https://blog.20061204.xyz/PicGo/2026/02/1ca3577a373d4f0ca1bf56d92d8c3e13.png){: .dark}

### 7.2 需部署服务,显示效果好

我通过vibe coding写了一个爬虫项目来爬取[github-contributions-chart](https://github.com/sallar/github-contributions-chart) 项目网站来获取图像。

<div class="box-tip" markdown="1">
<div class="title"> 工作原理 </div>

服务通过 Puppeteer 自动化访问 [github-contributions-chart](https://github.com/sallar/github-contributions-chart) 项目的网站，该网站提供了美观的 GitHub 贡献图表可视化界面。服务会：

1. 使用 Puppeteer 无头浏览器访问目标网站
2. 自动填入 GitHub 用户名和选择主题
3. 等待图表渲染完成
4. 截取 Canvas 生成高清 PNG 图片
5. 通过 Express API 提供图片访问接口

简单来说，这是一个将网页版图表转换为 API 服务的工具。

</div>

具体部署方案参考该[爬虫项目](https://github.com/cherry384719/GitHub-contribution-chart)的文档。

显示效果：

![more details](https://szn624334-github-chart-api.hf.space/cherry384719?theme=classic){: .light }

![more details](https://szn624334-github-chart-api.hf.space/cherry384719?theme=dracula){: .dark }


## 8. 文件结构
Jekyll博客内容基于每篇markdown文件，你可以在`_post`中设置子文件夹，但是不会渲染多级子文件夹结构。

在`_posts`文件夹中添加的markdown文件应命名为`YYYY-MM-DD-your-title.md`。

## 9. 代码存放
不应放在根目录下，建议新建仓库存放，链接到github上。[本博客代码仓库](https://github.com/cherry384719/Code_storage)。

对于Jupyter Notebook文件，还可以通过[https://nbviewer.org/](https://nbviewer.org/)这个网站进行链接预览。

> 代码块中的缩进要用**空格**而不是**制表符**，否则渲染出的代码缩进会过大。
{: .prompt-info}