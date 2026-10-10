# HtDot desktop releases / 桌面发行仓库

本仓库分发 HtDot 的 macOS、Windows 安装包、许可证和签名 OTA 更新。应用源码保存在独立的 HtDot 开发仓库。

## 下载开发测试版

[v0.1.2 开发测试版](https://github.com/VectorHo/HtDot-Releases/releases/tag/v0.1.2) 已公开，包含最新界面、桌面模型与 Computer 配置、MCP 入口和凭据等待时窗口响应修复。

| 设备 | 安装文件 |
| --- | --- |
| Apple Silicon Mac | 文件名包含 `macos-arm64` 的 `.dmg` |
| Intel Mac | 文件名包含 `macos-x64` 的 `.dmg` |
| Windows x64 | 文件名包含 `windows-x64` 的安装 `.exe` |

本版本先用于开发和 OTA 验收。构建、签名、公开下载与实机验收分别记录；Intel Mac 和 Windows 实机验收尚未完成。GitHub latest 用于客户端发现更新，不表示三平台正式验收通过。

macOS 安装包经过 Developer ID 签名和 Apple 公证。Windows 安装包未做 Authenticode，系统可能显示未知发布者。所有 OTA 包都有绑定版本的 Tauri updater 签名。

## 应用内更新

已安装发行版时，打开 **设置 → 模型与本地服务 → 应用更新 → 检查更新 → 安装更新并重启**。先完成活动任务、处理待审批，再安装。更新会验证签名、备份 SQLite，并在重启后核对完整应用和本地工作区。

客户端使用：

```text
https://github.com/VectorHo/HtDot-Releases/releases/latest/download/latest.json
```

无需 GitHub 登录。离线或更新源不可用时，本地工作仍可继续。HtDot Verify 是隔离测试包，不连接此更新源。不要把 `.sig` 或 OTA `.tar.gz` 当作普通安装文件。

OTA 管理页面后续属于独立云协同 Web 项目。目前 GitHub 直接承担文件分发；以后通过过渡客户端迁移地址并保留旧源兼容，无需等待云端页面才使用更新。

## English

[v0.1.2](https://github.com/VectorHo/HtDot-Releases/releases/tag/v0.1.2) is a **development test release** for macOS Apple Silicon, macOS Intel and Windows x64. It includes the latest UI, desktop connection settings and a fix for window responsiveness during system credential access.

Download the matching DMG or Windows EXE from the release. macOS packages are signed and notarized. Windows installers have no Authenticode signature. Every OTA package has a version-bound Tauri updater signature. Intel Mac and Windows device acceptance remain pending; GitHub latest does not imply production readiness.

To update an installed release, open **Settings → Model and local service → Application updates → Check for updates → Install update and restart**. Resolve active work and pending approvals first. Updates verify signatures, back up SQLite and check the installed version after restart.

The public feed above requires no GitHub login. Local work remains available offline. Verify packages do not use this feed. A future independent cloud project will provide release administration and can replace the update source through a transition client release.
