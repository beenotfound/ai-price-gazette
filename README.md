# AI 会员全球比价日报 · iPad / GitHub Pages

这是给 GitHub Pages 的部署目录，根目录的 `index.html` 就是完整网页。

## 最快上线（网页上传）

1. 在 GitHub 新建一个 **Public** 仓库，例如 `ai-price-gazette`
2. 打开仓库 → **uploading an existing file**
3. 把本文件夹里的**内容**（不是文件夹本身）全部拖进去
4. Commit changes
5. 仓库 **Settings → Pages**
   - Source：`Deploy from a branch`
   - Branch：`main`，目录 `/ (root)` → **Save**
6. 等 1–2 分钟，访问：

   `https://你的用户名.github.io/ai-price-gazette/`

## 用命令行上传

先在 GitHub 建空仓库（不要勾 README），然后在**工作区根目录**运行：

```powershell
powershell -ExecutionPolicy Bypass -File .\publish-ipad.ps1 -RepoUrl https://github.com/你的用户名/ai-price-gazette.git
```

脚本会初始化 `ipad-site` 的本地 git、提交、设置 remote 并 push。第一次 push 会弹 GitHub 登录。

## iPad 上当作 App

1. 用 **Safari** 打开上面的网址
2. 点分享按钮 → **添加到主屏幕**
3. 名称可以改成「AI 比价」
4. 之后从主屏幕打开，就是全屏独立窗口（PWA）
5. 第一次打开后，Service Worker 会缓存页面；之后断网也能打开并看内置牌价

> 如果主屏幕图标是空白：先刷新一次网页再重新添加；图标缓存有时需要几秒。

## 更新

修改主项目后：

```powershell
python build_pwa.py          # 重新生成此目录
cd ipad-site
git add .
git commit -m "update"
git push
```

GitHub Pages 大约 1 分钟后自动更新。

## 说明

- 页面是纯静态，GitHub Pages 免费托管
- 汇率/价格/AI 天梯口径见页面底部“这张报是怎么算出来的”
- `.nojekyll` 用于跳过 Jekyll 处理
