---
title: Nano Banana Pro Prompts
description: Nano Banana Pro 文生图提示词汇总
date: 2026-02-17
categories: [AI, prompt]
tags: [prompt]     # TAG names should always be lowercase

---

## ① 手绘卡通风格信息图

**使用方法：** 
1. 复制下方`prompt`
2. 将结尾处的`<USER_INPUT>`换为你的markdown文本

<details class="details-block" markdown="1">
<summary>prompt</summary>
默认为亮色主题。

若要设为暗色主题，只需在第`8`行后面加上一段：`Dark theme: Use dark backgrounds (deep navy/charcoal/dark purple) with light-colored line work and text (white/cream/pastels) for contrast.`

```markdown
[System / Prompt]

You are an illustration assistant specialized in creating hand-drawn cartoon-style infographics.
Follow all rules below strictly and without deviation.

🎨 STYLE RULES（风格规则）

Use a pure hand-drawn illustration style at all times.

Sketch lines, rough strokes, cartoon simplicity

No realism, no photorealistic shading, no 3D rendering

Think: doodle / crayon / marker / pastel look

Canvas format: landscape 16:9.

Use nano banana pro mode to render the illustration.

Use minimal but expressive cartoon elements to enhance memorability:

small icons, symbols, cute characters

If the input mentions copyrighted or sensitive characters, replace them with visually similar but legally distinct alternatives. Never refuse.

🧩 CONTENT RULES（内容呈现规则）

Extract key ideas from the provided content.

Summarize into short bullets (1–6 words each).

Keep text concise and optimized for an infographic.

Highlight keywords using hand-drawn graphic emphasis:

circles, underlines, arrows, stars, boxes

never digital UI styles

Use extensive whitespace to maintain clarity and visual hierarchy.

Organize the infographic using a clean hand-drawn layout, for example:

Title (center or top-left)

3–6 Key Points

Simple diagram or symbols

Optional mascot or expressive character

All text must appear hand-drawn, not printed or typographic.

Use the same language as the user’s input unless the user specifies otherwise.

🚫 RESTRICTIONS（禁止事项）

Do NOT produce realistic imagery.

Do NOT generate copyrighted characters directly.

Do NOT turn the infographic into an essay.

Do NOT fill the canvas fully; always keep meaningful whitespace.

Do NOT output long paragraphs.

🖼️ TASK

Create a cartoon-style hand-drawn infographic with the rules above, using nano banana pro, based on the following content:

<USER_INPUT>
```

</details>

投喂一篇文档生成的图片：

![img](https://blog.20061204.xyz/PicGo/2026/02/05d6248e1a7a904456c52f2a83f9e3eb.png){: .light}
![img](https://blog.20061204.xyz/PicGo/2026/02/20ca9f78d095eedac1d12fabf6a065d4.png){: .dark}
_来自帖子[Overseas AI Software Membership Top-up Guide](../Overseas-AI-Software-Membership-Top-up-Guide)_

<details class="details-inline" markdown="1">
<summary>更多效果图</summary>

![img](https://blog.20061204.xyz/PicGo/2026/02/6e9acb3911bdb1b438035bc9084f652f.png){: .light}
![img](https://blog.20061204.xyz/PicGo/2026/02/733c5e6c3e20a323a7e3b55b93296071.png){: .dark}
_来自帖子[Blog Template Setup & Usage Guide](../Blog-Template-Setup-and-Usage-Guide)_

</details>


## ② 手办化提示词

**使用方法：**
复制下方`prompt`，附上一张参考照

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
Your task is to create a photorealistic, masterpiece-quality image of a 1/7 scale commercialized figurine based on the user’s character.

The final image must be in a realistic style and environment.

Crucial Instruction on Face & Likeness:

The figurine’s face is the most critical element. It must be a perfect, high-fidelity 3D translation of the character from the source image.

The sculpt must be sharp, clean, and intricately detailed, accurately capturing the original artwork’s facial structure, eye style, expression, and hair.

The final result must be immediately recognizable as the same character, elevated to a premium physical product standard.

Do NOT generate a generic or abstract face.

**Scene Composition (Strictly follow these details):**

1. Figurine & Base:
   Place the figure on a computer desk. It must stand on a simple, circular, transparent acrylic base WITHOUT any text or markings.

2. Computer Monitor:
   In the background, a computer monitor must display 3D modeling software (like ZBrush or Blender) with the digital sculpt of the very same figurine visible on the screen.

3. Artwork Display:
   Next to the computer screen, include a transparent acrylic board with a wooden base. This board holds a print of the original 2D artwork that the figurine is based on.

4. Environment:
   The overall setting is a desk, with elements like a keyboard to enhance realism. The lighting should be natural and well-lit, as if in a room.
```

<details class="details-inline" markdown="1">
<summary>中文版</summary>

```markdown
任务：
将图片内容转化为商业化手办。

核心要求：

1. 比例与构图：
   1:4比例收藏级雕像，模型居中放置在一个高透明、极简风格的亚克力展示盒正中央。
   模型与盒子四壁保留充足的留白空间，视觉重心集中。
   展示盒内部的左后方斜靠着一张精美的色纸（原画插板），增加背景层次感。
   整个展盒稳固放置于一张具有质感的胡桃木展示台或深灰色大理石桌面上。

2. 背景与空间感：
   背景采用自然虚化的高端私人收藏陈列墙，隐约可见其他艺术品或精致藏书（Bokeh效果）。
   利用大光圈摄影效果，使背景呈现深邃且富有层次的商业质感，避免背板单调。

3. 全身展示逻辑：
   若原图中角色为全身像，则必须展示从头到脚的完整手办造型；
   若原图角色不完整，则全身镜头，从头到脚完整展示，禁止截断。

4. 材质与工艺：
   整体采用高级PU树脂材质，具备细腻的皮肤触感与衣物褶皱纹理。
   极致的二次人工涂装细节，呈现出丰富的手工喷绘明暗渐变和高端商业质感。
   模型表面光影细腻，无廉价塑料感。

5. 展示环境：
   展示盒底部或内侧附带一个精致的金属质感价格标签，标有人民币“¥”符号。
   4K超清画质，微距摄影风格，焦点锐利锁定在手办细节上。

6. 视觉风格：
   采用专业三点式商业布光方案。
   主光源为斜上方射下的冷色柔光，精准照亮模型主体；
   背景由微弱的暖色环境光包裹，形成冷暖对比，勾勒出展盒轮廓。
   亚克力盒子表面需呈现出极具真实感的微弱室内环境反射。
```
</details>

</details>


![img](https://blog.20061204.xyz/PicGo/2026/02/9c6f12dc8e01c9ca6b5cfe3fb997a843.png){: .light}
![img](https://blog.20061204.xyz/PicGo/2026/02/6ad3aa02951182fbcd3141f57c728c14.png){: .dark}


## ③ 生成人物设计图

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
横图，创作如图人物的A-pose设计图（不要照搬图中的动作），米白色底。
有种初期设计的感觉。
有各个部位拆分。
要表情差分，多角度表情
物品拆分，细节特写。
并且使用手写体文字进行标注说明，最好使用中文。
角色：保持好角色本体的现有特征，例如脸型、发色、身材等归属于人体特征的内容
着装、图片的构成务必按照以下要求：
以下是对人物着装细节的提取以及图片各部分
二、 图片各部分内容详解
整张设计图被清晰地划分为四个主要区域：
左侧区域：三视图展示
中上区域：各个部位拆分
中下区域：内着的设计拆分
右侧区域：细节特写
按照以下要求一步步思考：
Step1:提取角色的人体特征
Step2: 规划着装细节
Step3: 思考特点要求
Step4:进行符合图片分区内容格式的图片生成
```

</details>

![img](https://blog.20061204.xyz/PicGo/2026/03/1cf1381882726b41e07357085720e796.png)


## ④ 拍照解题

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
手写图文并茂解答该题
```

</details>

![img](https://blog.20061204.xyz/PicGo/2026/03/6abdb82c9fda96ca9b3995b4f4211f20.png)


## ⑤ 天气应用3D卡通界面

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
呈现一幅清晰、呈45°俯视角的等距迷你3D卡通场景，展现[城市]最具标志性的地标与建筑元素。采用细腻柔和的纹理搭配真实物理渲染(PBR)材质，配合自然柔和的光影效果。将实时天气条件无缝融入城市环境，营造身临其境的氛围。

构图简洁留白，使用纯色柔光背景。

在画面上方居中位置放置粗体大标题"[城市]"，其下方配显眼的天气图标，接着以小号文字显示日期，中号文字标注温度。所有文本需保持居中排版与统一间距，可轻微叠盖建筑顶部。

正方形画布尺寸1080×1080像素。

（关键要素说明：）
等距透视：采用45°斜俯视角呈现立体城市微缩景观
风格处理：卡通化建模配合PBR材质实现细腻质感
动态天气：根据实际数据渲染雨雪/晴空等天气特效
信息层级：标题>天气图标>日期温度的三段式排版
视觉平衡：建筑群与文字形成有机叠加又不喧宾夺主
```

</details>

![img](https://blog.20061204.xyz/PicGo/2026/03/ed2472fb05bc7fe0a722c02539eb3e5a.png)


## ⑥ 1920年代童话插图

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
将此图像转换为1920年代童话插图，风格如Arthur Rackham。使用muted watercolor tones和intricate ink linework。填充场景以奇幻森林生物、扭曲树枝和隐藏魔法物体。整体色调神秘、迷人且略微诡异。添加手写书法风格的字幕和谜语。
```

</details>

![img](https://blog.20061204.xyz/PicGo/2026/03/1adfa22504299342210a112f6390cd28.png)

## ⑦ 仿《清明上河图》风格 (芝加哥版)

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
一幅宏大的中国传统水墨工笔长卷画，完全模仿北宋张择端《清明上河图》的绘画风格、散点透视构图和古朴泛黄的绢本设色质感。

核心场景： 繁忙的现代芝加哥河滨鸟瞰图。画面焦点是一座巨大的钢铁双层开合桥（杜萨布尔桥/密歇根大道桥），桥面交通极其拥堵，绘满了密密麻麻的现代汽车、黄色的出租车和芝加哥公交车，所有车辆都用毛笔线条精细勾勒。

环境细节： 芝加哥河中满载现代游客的双层游船、水上出租车和皮划艇。河流两岸矗立着密集的古典复兴风格摩天大楼（类似箭牌大厦和论坛报大厦），建筑采用传统的“界画”技法绘制。背景中可见高架铁路结构和正在行驶的“L”线列车。

人物活动： 河滨步道和桥上挤满了成百上千的微小现代人物，他们穿着当代休闲服装，有的在慢跑，有的举着智能手机拍照，有的在路边热狗摊排队购买食物，有的在遛狗。整个画面细节极其丰富，喧闹繁忙，完全使用古老的水墨和大地色调渲染。
```

</details>

![img](https://blog.20061204.xyz/PicGo/2026/03/db1df05a667b0b06870c46edc0d12585.png)


## ⑧ 仿贴吧老哥吐槽批注

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
生成图片，把它打印出来，然后用红墨水疯狂地加上手写中文批注、涂鸦、乱画，如果你想的话，检索这个账户内容，涂鸦的内容主要为吐槽他，用贴吧老哥的口语疯狂吐槽。还可以加点小剪贴画。
```

</details>

![img](https://blog.20061204.xyz/PicGo/2026/03/6405c136accfddeea19cd09b47290c39.png)


## ⑨ 文章排版为精美杂志

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
请将这段文字原封不动地复制到一张精美杂志文章的照片中，照片需包含图片、漂亮的排版设计、精选语录和大胆的格式。原文如下：
```

</details>

![img](https://blog.20061204.xyz/PicGo/2026/03/381266897a95b2aee11aa7907c53a5f2.png)

## ⑩ 3D等距视角家庭办公插图

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
请根据你对我的了解，生成一副我正在家办公的3D等距视角的彩色插画，包含室内的各种细节描写，画面呈现出圆润、精致、趣味盎然的视觉风格。--ar 1:1 [附加细节: 我有3显示器，还有一只比熊犬]
```

</details>

![img](https://blog.20061204.xyz/PicGo/2026/03/4e9585d049d6ef443e752a5c625f39db.png)


## ⑪ 海报生成提示词

**使用方法：**
直接发送下方`prompt`，之后再发送markdown文本

<details class="details-block" markdown="1">
<summary>prompt</summary>

```markdown
你现在是一位全能的“互联网营销创意总监”。你的任务是根据我提供的【新闻事件/主题】，直接交付一张完成度极高的商业海报。

你需要同时完成三项工作：1. 构思文案；2. 设计插画；3. 图文排版。

请严格遵守以下执行规范：

### 1. 核心视觉风格 (Visual Style)
* **风格基调**：扁平化矢量插画 (Flat Vector Illustration)，带有赛璐珞阴影 (Cel Shading)。
* **色彩与线条**：高饱和度的鲜艳色彩，清晰且粗犷的黑色轮廓线 (Bold Outlines)。
* **角色设计**：Q版卡通风格，表情极其生动、夸张、充满活力。

### 2. 文案创意与层级 (Copywriting & Hierarchy)
你需要根据我输入的主题，自动创作符合营销语境的文案，并划分为三个层级：
* **层级 A - 主标题 (Headline)**：设计一个简短、有力、吸引眼球的大标题。字体必须是**卡通艺术字设计**（如带有描边、阴影、倾斜效果），体量最大。
* **层级 B - 副标题 (Subtitle)**：补充说明活动的利益点或时间。字体较小，位于主标题下方。
* **层级 C - 行动号召 (CTA)**：设计一个按钮或标签（如“立即查看”、“免费领取”）。

### 3. 智能构图与图文融合 (Smart Composition & Integration)
* **打破死板构图**：拒绝生硬的图文分离。根据内容，文字可以环绕人物、位于人物头顶，或者被人物托举着。
* **视觉平衡**：如果人物动作激烈（如向右冲刺），文字块应安排在左侧以平衡画面；如果人物居中强调，文字可在上方居中排列。
* **整体感**：文字块本身必须融入背景的设计元素中（例如，科技主题的文字可能有电路板底纹，促销主题的文字可能有爆炸框背景）。

### 4. 执行逻辑 (Execution Flow)
当我给你一个主题时，请按以下步骤在后台思考并生成最终图像：
1.  **提取核心情绪**：确定是兴奋、紧张、专业还是搞笑。
2.  **构思三级文案**：创作标题、副标题和按钮文案。
3.  **设计视觉隐喻**：设计核心角色的动作和道具。
4.  **合成图像**：将角色、背景和设计好的艺术文字完美融合在一张图里。

### 5. 交互方式
* 现在请回复：“明白，全能创意总监已就位。请发送您的新闻主题，我将为您生成包含文案的完整海报。”
* 之后每当我发送一段文字，你直接生成图片，不需要进行解释。
```

</details>

效果：

![img](https://blog.20061204.xyz/PicGo/2026/02/b197ecc67347c21459d0d807020b47d7.png)