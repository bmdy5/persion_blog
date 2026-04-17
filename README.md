# Personal Blog – Liang Ge

## 项目概述

单页个人博客，使用纯 HTML + Tailwind CDN，内容通过本地 `data/blog.json` 动态渲染。实现了卡片翻转、滚动视差、微动按钮等交互效果，并部署在 Vercel，域名 **xiaoliang.tech**。

## 本地运行

```bash
# 克隆仓库（如果尚未克隆）
git clone <your-repo-url>
cd personal-blog

# 打开 HTML 文件（直接在浏览器中打开）
open code.html   # macOS
# 或在 VS Code 中使用 Live Server 插件
```

确保 `data/blog.json` 已存在（已在项目中创建示例数据），打开 `code.html` 即可看到页面渲染。

## 部署到 Vercel

1. 将项目推送到 GitHub（或其他 Git 平台）。
2. 登录 Vercel，点击 **New Project**，选择对应仓库。
3. Vercel 会自动检测为 **Static Site**，无需额外构建配置。
4. 部署完成后，在 Vercel 项目设置中添加自定义域名 **xiaoliang.tech**，并在域名提供商（如 Cloudflare）配置 DNS 指向 Vercel 提供的记录。
5. 部署成功后，访问 `https://xiaoliang.tech` 即可查看博客。

## 未来迭代方向

- 添加站内搜索（lunr.js）
- 集成评论系统（Giscus / Utterances）
- 支持 Markdown 文件自动转换
- 替换本地 JSON 为 Notion 或 Headless CMS 同步

---

*本项目遵循 MIT 许可证。*
