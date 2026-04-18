# Tasks: Personal Blog Enhancement

## Implementation Steps

1. **准备资源**
   - 确认头像文件名并放入 `img/`（如 `my_photo.jpg`）。
   - 下载并保存工具图标为 SVG，放入 `img/tools/`（`openmaid.svg`, `buffett.svg`, `notebooklm.svg`, `stitch.svg`, `jetbrains.svg`）。
2. **Hero 区块**
   - 在 `index.html` 顶部新增头像容器，使用 `rounded-full`、`drop-shadow`、可选 `backdrop-filter: blur(8px)` 实现玻璃化相框。
   - 添加简短自我介绍文字。
3. **时间轴（人生阶段）**
   - 创建垂直时间轴结构，左侧年份/阶段，右侧卡片。
   - 卡片使用 `bg-[#fffdec] border-4 border-inverse-surface`，悬停时 `translate-x-[2px] translate-y-[2px]`，背面展示遗憾文字（手写体）。
   - 内容使用已优化的文字（见提案）。
4. **项目/产品展示网格**
   - 在 `#projects-container` 中插入网格 `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`。
   - 每个卡片复用现有 `.card`、`.card-inner` 翻转动画，前面显示标题、描述、技术标签，背面放置链接按钮。
5. **常用工具列表**
   - 在页脚新增横向滚动容器 `flex overflow-x-auto gap-4`。
   - 为每个工具生成卡片，内部放置 SVG 图标、名称、链接按钮，悬停时背景变 `#a80096`、文字变白并轻微缩放。
6. **样式微调**
   - 在 `tailwind.config` 中加入 `#ffff00`、`#a80096`（若未定义）。
   - 为头像、工具卡片添加 `rounded-lg`（8 px）和 `backdrop-filter` 实现玻璃化。
   - 确保所有交互使用 `transition duration-200`。
7. **SEO 与可访问性**
   - 为每个新章节添加 `<h2>`（唯一的 `<h1>` 已在页面顶部）。
   - 为图片添加 `alt` 文本，链接添加 `title`。
   - 确保所有交互元素拥有唯一 `id`。
8. **测试与调试**
   - 本地运行 `npm run dev`（或直接打开 `index.html`），检查头像圆形、时间轴、卡片翻转、工具滚动是否正常。
   - 在不同视口（mobile、tablet、desktop）下验证响应式布局。
   - 确认 Vercel 部署后图片路径正确（相对路径 `img/...`）。
9. **提交 & 部署**
   - 将所有修改 `git add .`、`git commit -m "feat: personal blog enhancement"`、`git push`。
   - Vercel 自动部署，检查是否仍然返回 200 并显示新内容。
## 补充任务

- [ ] 确认头像是否使用玻璃化相框；若是，添加 `backdrop-filter` 样式并在任务中标记。
- [ ] 引入手写体字体（Caveat）并在时间轴卡片背面使用；更新 Tailwind 配置或在 `<head>` 加载。
- [ ] 为项目展示准备 `projects.json`（或在 `blog.json` 中加入 `type: "project"`），并在任务 4 中补充数据准备步骤。
- [ ] 为工具卡片添加 `target="_blank"`、`rel="noopener"`，并在悬停时显示 tooltip（简短描述）。
- [ ] 为 Hero 区块添加移动端布局切换（头像上方、文字下方），使用 Tailwind 响应式类。
- [ ] 为时间轴在窄屏下实现水平滚动或折叠（使用 `overflow-x-auto`）。
- [ ] 为所有图片使用 `loading="lazy"`，并将头像、工具图标转为 WebP 格式。
- [ ] 为交互元素添加键盘焦点样式 `focus-visible:ring-2`，并补充必要的 ARIA 标签。
- [ ] 将时间轴每阶段文字压缩至 1‑2 行，保持卡片高度一致。
- [ ] 部署后运行 Lighthouse CI，记录并优化 CLS、LCP、FCP 等关键指标。
## 完成标记
- [x] 头像文件准备完毕
- [ ] 工具图标下载完毕
- [ ] Hero 区块实现
- [ ] 时间轴实现
- [ ] 项目网格实现
- [ ] 工具列表实现
- [ ] 样式与交互调试完成
- [ ] SEO 检查通过
- [ ] 本地测试通过
- [ ] 提交并部署
