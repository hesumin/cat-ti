# NBTI

把 CatTI、MouTI 和 DogTI 放进同一个仓库后的统一项目。

## 项目结构

```text
NBTI/
├─ cat-ti/
│  └─ index.html
├─ mou-ti/
│  └─ index.html
├─ dog-ti/
│  └─ index.html
├─ index.html
└─ .github/workflows/
   ├─ deploy-nbti.yml
   ├─ deploy-cat-ti.yml
   ├─ deploy-mou-ti.yml
   └─ deploy-dog-ti.yml

```


## 约定后的发布流程

以后统一走这条链路：

1. 先在本地修改 `cat-ti/index.html`、`mou-ti/index.html` 或 `dog-ti/index.html`
2. 提交并推送到 GitHub 仓库 `https://github.com/hesumin/NBTI`
3. 由 GitHub Actions 自动把对应目录发布到 Cloudflare Pages


## 已落地的自动部署方式

仓库内已经增加四个工作流：

- `.github/workflows/deploy-nbti.yml`
- `.github/workflows/deploy-cat-ti.yml`
- `.github/workflows/deploy-mou-ti.yml`
- `.github/workflows/deploy-dog-ti.yml`

触发逻辑：

- 修改根目录 `index.html` 或任一动物子目录并推送到 `main` → 自动部署 NBTI 根站到 `nb-ti`


- 修改 `cat-ti/**` 并推送到 `main` → 自动部署 `cat-ti`
- 修改 `mou-ti/**` 并推送到 `main` → 自动部署 `mou-ti`
- 修改 `dog-ti/**` 并推送到 `main` → 自动部署 `dog-ti`
- 也支持在 GitHub Actions 页面手动触发



## GitHub 需要补的 Secrets

在仓库 `hesumin/NBTI` 的 Settings → Secrets and variables → Actions 中添加：

- `CLOUDFLARE_API_TOKEN`
- `CLOUDFLARE_ACCOUNT_ID`

其中：

- `CLOUDFLARE_API_TOKEN` 需要具备 Cloudflare Pages 编辑权限
- `CLOUDFLARE_ACCOUNT_ID` 填你的 Cloudflare 账户 ID

## Cloudflare Pages 对应项目名

### NBTI
- Project name: `nb-ti`
- Deploy directory: `.`
- Branch: `main`
- 首次运行会在 GitHub Actions 中自动检查并创建 `nb-ti` 的 Cloudflare Pages 项目



### CatTI
- Project name: `cat-ti`
- Deploy directory: `./cat-ti`
- Branch: `main`

### MouTI
- Project name: `mou-ti`
- Deploy directory: `./mou-ti`
- Branch: `main`

### DogTI
- Project name: `dog-ti`
- Deploy directory: `./dog-ti`
- Branch: `main`
- 首次运行会在 GitHub Actions 中自动尝试创建 `dog-ti` 的 Cloudflare Pages 项目


## 页面入口

- NBTI 入口页: `index.html`
- CatTI: `cat-ti/index.html`
- MouTI: `mou-ti/index.html`
- DogTI: `dog-ti/index.html`


