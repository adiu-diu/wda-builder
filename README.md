# wda-builder

用 GitHub 免费 macOS 云构建机，把官方 [appium/WebDriverAgent](https://github.com/appium/WebDriverAgent) 编译成**未签名**的 `WebDriverAgent.ipa`。
不需要你自己的 Mac，也不需要任何第三方不明安装包。编译出的 ipa 之后用 **Sideloadly**（Windows）自签安装到 iPhone。

## 用法

1. 注册 / 登录 GitHub（免费）。
2. 新建一个空仓库（名字随意，例如 `wda-builder`）。
3. 把这个文件夹整体推上去：
   ```bash
   cd wda-builder
   git init
   git add .
   git commit -m "Add WDA build workflow"
   git branch -M main
   git remote add origin https://github.com/<你的用户名>/wda-builder.git
   git push -u origin main
   ```
4. 进仓库 **Actions** 标签 → 看到 `Build WebDriverAgent IPA` → 点 **Run workflow** → 等约 5 分钟。
5. 构建完成后：
   - 从 **Artifacts** 下载 `WebDriverAgent-IPA`（里面是 `WebDriverAgent.ipa`），或
   - 从 **Releases** 下载 `wda-<运行号>` 里的 ipa。
6. 拿到 `WebDriverAgent.ipa` 后，用 Sideloadly 自签安装（见上级目录 `部署指南.md` 的路径 A）。

## 说明

- 产物是**未签名**的 ipa，签名由 Sideloadly + 你的免费 Apple ID 完成。
- 免费 Apple ID 签名有效期 **7 天**，到期需重签 / 重新编译。
- 源码来自官方 appium WDA，可信；整个流程只依赖 GitHub 官方 runner 与官方仓库。
