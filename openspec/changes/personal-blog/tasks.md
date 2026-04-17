# Tasks: Personal Blog (personal-blog)

## 目标
实现一个 **单页** 个人博客，使用 **纯 HTML + Tailwind CDN**，内容通过本地 `data/blog.json` 动态渲染，具备卡片翻转、滚动视差、微动按钮等交互，并部署到 Vercel（域名 `xiaoliang.tech`）。

## 任务列表（按执行顺序）

| # | 任务描述 | 所属模块 | 估算时间 | 完成标记 |
|---|----------|----------|----------|----------|
| 1 | **创建 data 目录 & 示例 JSON**<br>在项目根目录新建 `data/`，并添加 `blog.json` 示例（标题、slug、tags、content、cover）。 | 数据 | 15 min | ✅ |
| 2 | **在 HTML 中添加锚点容器**<br>在 `code.html`（或 `index.html`）的 `<main>` 中插入 `<section id="plan">` 与 `<section id="projects">`，并在 Header 导航添加对应 `<a href="#plan">`、`<a href="#projects">`。 | 结构 | 10 min | ✅ |
| 3 | **编写渲染脚本**<br>在 `<script>` 末尾添加 `DOMContentLoaded` 监听，使用 `fetch('/data/blog.json')` 读取数据，依据 `tags` 将卡片插入对应容器。 | 逻辑 | 20 min | ✅ |
| 4 | **实现卡片组件**<br>创建卡片 HTML 模板（`<div class="card">…`），包括 `.card-inner`、`.card-front`、`.card-back`（可留空），并在 JS 中填充 `title`、`content`。 | UI | 25 min | ✅ |
| 5 | **添加卡片翻转 CSS**<br>在 `<style>` 中加入 3D 翻转样式：`perspective`, `transform-style`, `backface-visibility`, `hover` 触发 `rotateY(180deg)`。保持硬边框、硬阴影、0 圆角。 | 动效 | 10 min | ✅ |
| 6 | **实现滚动视差**<br>为 Hero 区块设置 `background-attachment: fixed`，并在 JS 中监听 `scroll`，对标题使用 `translateY(window.scrollY * 0.2)`。 | 动效 | 15 min | ✅ |
| 7 | **复用微动按钮**<br>确认现有按钮的 Tailwind 类（`hover:translate-x-[2px] hover:translate-y-[2px] shadow-[4px_4px_0px_0px_#0d0f0d]`）在新卡片、CTA 中保持一致。 | 交互 | 5 min | ✅ |
| 8 | **SEO 基础**<br>在 `<head>` 添加 `<title>Liang Ge – Personal Blog</title>` 与 `<meta name="description" content="Personal blog showcasing planning, projects, and thoughts.">`，使用语义化标签（`<header>`、`<nav>`、`<main>`、`<section>`、`<article>`）。 | SEO | 10 min | ✅ |
| 9 | **本地测试**<br>在本地打开 `code.html`，检查 JSON 渲染、卡片翻转、视差、按钮动画是否正常。使用 Chrome DevTools 检查网络请求是否成功。 | 测试 | 15 min | ✅ |
|10| **提交 & Vercel 部署**<br>将所有改动 `git add . && git commit -m "feat: personal blog MVP"` 推送至 GitHub，Vercel 自动构建并部署。确认 `https://xiaoliang.tech` 正常访问。 | 部署 | 10 min | ✅ |
|11| **后续迭代计划**<br>记录后续可选功能：站内搜索（lunr.js）、评论系统（Giscus/Utterances）、RSS、Markdown → HTML 转换、Notion 同步。 | 规划 | 5 min | ✅ |

**总计预计时间**：约 **2 小时 15 分钟**（不含后续功能实现）。
