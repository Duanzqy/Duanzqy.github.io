# 个人主页内容填写说明

这份文档用于说明当前主页里哪些内容已经接好、之后你应该改哪些文件，以及每个模块应该怎么自己填。

## 目前已经完成的内容

- 首页主文件：`index.html`
- 样式文件：`assets/css/style.css`
- 当前头像：`assets/Nero.jpg`
- 论文区已经填入两篇论文主页和论文链接
- 内容草稿文件：`index.md`

当前真正决定网页展示效果的是 `index.html`，不是 `index.md`。

## 你以后最常改的文件

- `index.html`
  - 改首页显示内容
  - 改论文、博客、项目、推荐阅读、联系方式
- `assets/css/style.css`
  - 改颜色、字体、卡片样式、排版、响应式效果
- `assets/Nero.jpg`
  - 如果你想换头像，直接把新图片替换成这个文件名，最省事

## 1. 如何更换头像

当前首页头像位置在 `index.html` 里这行附近：

```html
<img src="assets/Nero.jpg" alt="Nero avatar" />
```

你有两种改法：

### 方法 A：直接替换同名文件

- 把你想用的新头像覆盖 `assets/Nero.jpg`
- 不需要改 `index.html`

### 方法 B：换文件名

- 把图片放到 `assets/` 目录下，比如 `assets/my-avatar.png`
- 然后把 `index.html` 里的图片地址改成：

```html
<img src="assets/my-avatar.png" alt="My avatar" />
```

## 2. 如何修改论文信息

论文展示在 `index.html` 的 `Selected Publications` 区域。

每篇论文的结构大概是这样：

```html
<article class="publication-item section-frame">
  <p class="card-meta">CVPR 2026</p>
  <h3>论文标题</h3>
  <p>作者列表</p>
  <div class="publication-footer">
    <span>单位或补充信息</span>
    <span>年份</span>
    <span>
      <a href="项目主页">Project Page</a> /
      <a href="论文链接">Paper</a>
    </span>
  </div>
</article>
```

你以后只需要替换这几个位置：

- `card-meta`：会议名，比如 `CVPR 2026`、`ICCV 2025`
- `h3`：论文标题
- 作者列表
- 单位 / 简短说明
- 年份
- `Project Page` 和 `Paper` 链接

如果以后有代码仓库，也可以改成：

```html
<span>
  <a href="项目主页">Project Page</a> /
  <a href="论文链接">Paper</a> /
  <a href="代码链接">Code</a>
</span>
```

## 3. 如何填写博客内容

博客展示在 `Recent Writing` 区域。

每张博客卡片长这样：

```html
<article class="feature-card writing-card featured">
  <p class="card-meta">Blog Post - Placeholder</p>
  <h3>Writing Placeholder 01</h3>
  <p>这里是博客摘要</p>
  <a href="#">Draft slot</a>
</article>
```

你要改的地方：

- `card-meta`
  - 可以写成 `Blog Post`、`Reading Note`、`Research Note`
- `h3`
  - 改成文章标题
- 摘要段落
  - 用 1~2 句话说明这篇文章讲什么
- 最后的链接
  - 如果文章已经有单独页面，就填真实链接
  - 如果还没写完，可以先保留 `#`

例如：

```html
<p class="card-meta">Reading Note</p>
<h3>Diffusion Models 入门阅读笔记</h3>
<p>整理几篇适合入门 diffusion 的论文与博客，并补充自己的理解。</p>
<a href="posts/diffusion-notes.html">Read more</a>
```

## 4. 如何填写项目内容

项目展示在 `Projects` 区域。

结构是：

```html
<article class="feature-card project-card">
  <p class="card-meta">Coming Soon</p>
  <h3>Project Placeholder 01</h3>
  <p>A future public project will be introduced here.</p>
</article>
```

你可以改成：

- 项目状态：`Coming Soon` / `Open Source` / `In Progress`
- 项目标题
- 一句简介

如果以后想加 GitHub 链接，可以在卡片里再加一行：

```html
<a href="https://github.com/你的仓库">GitHub</a>
```

## 5. 如何填写推荐阅读

推荐阅读展示在 `Reading / Recommendations` 区域。

适合放：

- 你推荐的论文
- 某个方向的阅读路线
- 工具资源整理
- 一些值得读的博客或教程

结构很简单：

```html
<article class="section-frame recommendation-item">
  <h3>标题</h3>
  <p>一两句说明这条推荐的价值</p>
</article>
```

## 6. 如何修改联系方式

联系方式在 `index.html` 最底部 `Contact` 区域。

当前是：

```html
<li><a href="mailto:byguo@mail.ustc.edu.cn">byguo@mail.ustc.edu.cn</a></li>
<li><a href="#">GitHub link to be added</a></li>
<li><a href="#">Google Scholar / CV later</a></li>
```

你可以直接替换成真实链接：

```html
<li><a href="mailto:byguo@mail.ustc.edu.cn">byguo@mail.ustc.edu.cn</a></li>
<li><a href="https://github.com/你的用户名">GitHub</a></li>
<li><a href="https://scholar.google.com/...">Google Scholar</a></li>
```

## 7. 如果你想继续美化页面

主要改 `assets/css/style.css`。

你最常会改这些：

- 颜色变量：文件最上面的 `:root`
- 卡片圆角：`--radius-lg`、`--radius-md`
- 页面主色：`--accent`、`--green-deep`
- Hero 大标题大小：`.hero h1`
- 博客卡片布局：`.writing-grid`

比如你想改主色，可以修改：

```css
--accent: #8f6444;
--green-deep: #31453a;
```

## 8. 如何本地预览

在仓库目录运行：

```bash
python -m http.server 8000
```

然后浏览器打开：

```text
http://127.0.0.1:8000/index.html
```

## 9. 修改后如何提交

```bash
git add .
git commit -m "Update homepage content"
git push
```

## 10. 我建议你接下来自己优先填哪些内容

建议顺序：

1. 把 GitHub 和 Google Scholar 链接补上
2. 把博客区 3 张卡片改成真实标题
3. 把 About 区改成更像你本人的简介
4. 如果有 CV 链接，再加到 Contact
5. 后续再拆单独的博客页和论文页
