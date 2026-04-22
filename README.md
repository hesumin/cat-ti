# NBTI

把 CatTI 和 MouTI 放进同一个仓库后的统一项目。

## 项目结构

```text
NBTI/
├─ cat-ti/
│  └─ index.html
├─ mou-ti/
│  └─ index.html
└─ index.html
```

## 约定后的发布流程

以后统一走这条链路：

1. 先在本地修改 `cat-ti/index.html` 或 `mou-ti/index.html`
2. 提交并推送到 GitHub 仓库 `https://github.com/hesumin/NBTI`
3. 由 GitHub Actions 自动把对应目录发布到 Cloudflare Pages

## 已落地的自动部署方式

仓库内已经增加两个工作流：

- `.github/workflows/deploy-cat-ti.yml`
- `.github/workflows/deploy-mou-ti.yml`

触发逻辑：

- 修改 `cat-ti/**` 并推送到 `main` → 自动部署 `cat-ti`
- 修改 `mou-ti/**` 并推送到 `main` → 自动部署 `mou-ti`
- 也支持在 GitHub Actions 页面手动触发

## GitHub 需要补的 Secrets

在仓库 `hesumin/NBTI` 的 Settings → Secrets and variables → Actions 中添加：

- `CLOUDFLARE_API_TOKEN`
- `CLOUDFLARE_ACCOUNT_ID`

其中：

- `CLOUDFLARE_API_TOKEN` 需要具备 Cloudflare Pages 编辑权限
- `CLOUDFLARE_ACCOUNT_ID` 填你的 Cloudflare 账户 ID

## Cloudflare Pages 对应项目名

### CatTI
- Project name: `cat-ti`
- Deploy directory: `./cat-ti`
- Branch: `main`

### MouTI
- Project name: `mou-ti`
- Deploy directory: `./mou-ti`
- Branch: `main`


## 页面入口

- CatTI: `cat-ti/index.html`
- MouTI: `mou-ti/index.html`
- 根目录导航页: `index.html`
