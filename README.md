# luci-app-easytier

本项目为 [EasyTier/luci-app-easytier](https://github.com/EasyTier/luci-app-easytier) 的 Fork 分支，已同步最新代码并优化了自动化构建流程。

依赖 `kmod-tun` 需要先在系统软件包里安装好。

### 🚀 快速开始 (GitHub Actions)

1. 右上角 **Fork** 克隆本项目。
2. 到 **Actions** 页面，选择 `Build-OpenWrt-EasyTier`。
3. 点击 **Run workflow** 手动触发：
   - **tag**: 填写版本号（如 `v2.5.0`），留空则不发布 Release。
   - **text**: 填写发布说明。
4. 编译完成后，在 **Releases** 页面下载对应架构的压缩包。

### 📦 版本说明

为了适配不同存储空间的设备，本项目同时提供两个版本：
- **Full 版**: 包含 `easytier-web` 控制台，功能最全，推荐 Flash 空间大于 32MB 的设备使用。
- **Lite 版**: 移除了 Web 控制台，仅保留 VPN 核心功能，适合 Flash 空间小的设备。

### 📥 安装方法

将下载的包上传到 OpenWrt 的 `/tmp` 目录。

#### OpenWrt 23.05 及旧版 (ipk)
```bash
opkg install /tmp/luci-app-easytier_*.ipk
```

#### OpenWrt SNAPSHOT / 新版 (apk)
```bash
apk add --allow-untrusted /tmp/luci-app-easytier_*.apk
```

> **注意**：本插件不包含 `easytier-core` 二进制程序。安装后请在 LuCI 界面上传程序，或通过 `opkg install easytier` 安装官方二进制。

### 🔄 同步上游

如果你想让你的 Fork 保持最新，建议执行以下命令：
```bash
git remote add upstream https://github.com/EasyTier/luci-app-easytier.git
git fetch upstream
git reset --hard upstream/main
git push origin main --force
```
*(注意：这会覆盖你的本地修改。建议在同步后重新配置你的 build.yml)*
