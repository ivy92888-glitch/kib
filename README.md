# Kib · 上传到 GitHub Pages 教程

把 `kibble-kids-app` 整个文件夹传到 GitHub，开 Pages 后外甥女手机就能打开
`https://<你的用户名>.github.io/<仓库名>/` 独立链接，和主站 interview-pass 完全无关。

## 第 0 步：上传前准备（一次解压）

1. 下载 / 取得 `kibble-kids-app.tar.gz`（本目录里已打好的压缩包）。
   - 它是一整个文件夹 `kibble-kids-app/`，内含 238 个文件。
   - Windows 用「WinRAR / 7-Zip / Bandizip」右键 → 解压；macOS 双击即可。
2. 解压后得到 `kibble-kids-app/` 文件夹（里面是 index.html、sw.js、manifest.json、
   assets/、scenes/、pets/、icons/ 等）。**不要删任何文件**。
3. 该文件夹里**没有 `.git`**，干净。

> 若不想用压缩包，也可以直接拖本地的 `D:\WorkBuddyDoc\kibble-kids-app` 文件夹
> （但拖之前请确认里面没有 `.git` 子目录——网页上传会把它一起传上去，
> 虽然不致命，但仓库里会有冗余）。

## 第 1 步：在 GitHub 建空仓库 + 网页上传（全程浏览器，不用 git 命令、不用密码）

1. 登录 GitHub → 右上角 **「+」→「New repository」**。
2. Repository name 填 `kib`（或你喜欢的名字），可见性选 **Public**。
3. **不要勾选** "Add a README"、.gitignore、license——保持空仓库。
4. 点 **Create repository**。
5. 进仓库页 → 点 **Add file → Upload files**（或 "上传文件" 按钮）。
6. 把 `kibble-kids-app/` 文件夹里的**所有文件和子文件夹**拖进上传框。
   - 可以直接拖那个文件夹本身，GitHub 会保留内部结构。
   - 注意：网页上传单次一般可上传几百个文件，但 **74MB / 238 个文件可能慢，
     耐心等它转圈完成**；若中途卡死，分两次传（先传文件夹 assets/、scenes/ 等大的，
     再传根目录的 index.html / sw.js / manifest.json 等）。
7. 滚动到底部，点 **Commit new files**。

## 第 2 步：开通 GitHub Pages

1. 仓库页左侧菜单 → **Settings**（设置）→ **Pages**。
2. 在 "Build and deployment" 区域：
   - **Source** 选 **Deploy from a branch**（从分支部署）。
   - **Branch** 选 `main`，文件夹选 `/ (root)`。
   - 点 **Save**。
3. 页面顶部会出现「Your site is live at `https://<你的用户名>.github.io/kib/`」。
   - 首次部署需 1–3 分钟，刷新几次再打开。

## 第 3 步：手机验收

1. 外甥女手机浏览器打开那个 `https://...github.io/kib/` 链接。
2. 页面顶部标题应是「**Kib · 今天学一点，宠物长一点**」。
3. 想当 App 用：手机浏览器菜单 →「**添加到主屏幕**」→ 主屏出现 **Kib** 图标。
4. 第一次进会弹 Service Worker / PWA 提示，点允许即可，之后离线也能玩。

## 验收清单（把这条发回给我核对）

- [ ] 仓库地址：`https://github.com/<用户名>/<仓库名>`
- [ ] Pages 链接：`https://<用户名>.github.io/<仓库名>/`
- [ ] 打开链接，浏览器标题 =「Kib · 今天学一点，宠物长一点」
- [ ] 主站 `https://interview-pass.app.workbuddy.host/` 仍正常（version.txt = 2026.10.13n）

## 常见坑

- **网页上传 74MB 卡死**：分两次传，或改用 git 命令推送（下面备用方案）。
- **Pages 一直 Not found**：等满 3 分钟再刷；或检查 Branch 是否选的 `main`、
  文件夹是否 `/ (root)`。
- **上传后仓库里混进了 `.git` 目录**：删掉无妨，重新推一次。
- **国内打不开 github.io**：需科学上网；外甥女手机若在国内且打不开，
  换 Cloudflare Pages / Netlify（同样是免费静态托管，流程类似）。

## 备用：git 命令推送（适合网页上传不顺时）

在终端里（Windows 用 Git Bash）：

```bash
cd /d/WorkBuddyDoc/kibble-kids-app

# 第一次推（建仓库后）：把 <仓库地址> 换成 https://github.com/<用户名>/kib.git
git remote add origin https://github.com/<用户名>/kib.git
git push -u origin main

# 若提示登录，Git 会弹 GitHub 网页登录框（扫码或输密码），凭证不经过我
```

推完同样走第 2、3 步。

## 安全备注

- 全程不需要把 GitHub 账号密码告诉任何人 / 任何工具。
- 本目录是**纯静态**（无外链、无后端、无云服务），只存 localStorage 本地进度。
- 主站 A（interview-pass）已恢复 13n，与本次上传互不影响。
