# Clear Style

HTML 样式清理工具：去除内联样式与不安全属性，支持保留表格样式等选项。纯前端运行，可本地使用或远程部署。

## 本地运行

- **静态**：直接浏览器打开 `index.html`，或任意静态服务器（如 `npx serve .`）。
- **Node**：`node server.js`，默认访问 <http://localhost:3000>；可通过环境变量 `PORT` 改端口。

## 远程部署

### 1. 静态托管（推荐，零配置）

把本仓库推送到 Git 后，在对应平台「连接仓库」并发布根目录即可。

| 平台 | 说明 |
|------|------|
| **Netlify** | 连接 GitHub/GitLab，Build 留空或 `publish: .`，自动使用根目录 `netlify.toml`。 |
| **Vercel** | 连接仓库，Framework 选 Other，根目录已包含 `vercel.json`。 |
| **Cloudflare Pages** | 连接 Git，Build 命令留空，输出目录填 `.` 或 ` /`。 |
| **GitHub Pages** | 在仓库 Settings → Pages 里，Source 选分支，目录选 `/ (root)`，首页即 `index.html`。 |

### 2. Node 服务器（VPS / PaaS）

适用于 Railway、Render、Heroku 等支持 Node 的环境：

- 根目录已有 `package.json`、`server.js`、`Procfile`。
- 部署时安装依赖（若需要）：`npm install`（当前无依赖，可不执行）。
- 启动命令：`node server.js` 或 `npm start`。
- 平台会通过 `PORT` 注入端口，无需改代码。

### 3. 手动部署到自有服务器

```bash
# 克隆或上传项目后
cd clear-style
node server.js
# 或使用 pm2: pm2 start server.js --name clear-style
```

如需对外 80 端口，可用 Nginx 反代本地 `http://127.0.0.1:3000`。
