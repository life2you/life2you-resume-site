# life2you-resume-site

赵军的个人在线简历站。站点是一个纯静态 Vue 3 页面，可通过 GitHub Pages 发布。

页面重点呈现公开可表达的职业成果：内部财务系统研发管理、利润统计性能重构、实际经营利润计算体系，以及 FlowBridge 的 AI 研发协同实践。

## 本地开发

```bash
npm install
npm run dev
```

构建生产版本：

```bash
npm run build
npm run preview
```

## 内容修改

主要文案、职业经历、项目和技术栈集中在 `src/resume-data.js`，优先修改这里，不需要调整页面结构。

- 请确认公开的信息只包含你愿意对外披露的事实。
- 不要将公司内部域名、客户名称、代码路径、表结构、访问凭据或未公开架构细节放到页面中。
- 当前联系入口为 GitHub；若要添加邮箱、微信或 PDF 下载链接，请只使用明确允许公开的联系方式。

## GitHub Pages 发布

仓库中的 `.github/workflows/deploy-pages.yml` 会在 `main` 分支推送后构建并发布站点。

首次启用时，在 GitHub 仓库中打开：

`Settings` → `Pages` → `Build and deployment` → `Source` → 选择 `GitHub Actions`

推送后，页面地址为：

`https://life2you.github.io/life2you-resume-site/`

Vite 配置使用相对资源路径，因此后续绑定自定义域名时不需要改前端构建路径。只需在 GitHub Pages 设置中填写域名，并按 GitHub 提示在域名 DNS 中添加对应记录。
