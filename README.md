# HtDot desktop releases / 桌面发行仓库

本仓库分发 HtDot 的 macOS、Windows 安装包、许可证和签名 OTA 更新。应用源码保存在独立的 HtDot 开发仓库。

## 下载开发测试版

[v0.1.5 Apple Silicon 开发测试版](https://github.com/VectorHo/HtDot-Releases/releases/tag/v0.1.5) 已公开，修复“模型设置测试成功，但对话历史加载失败”的桌面传输问题。本次只构建 M 芯片 Mac，提供签名、公证 DMG 和签名 OTA；无需重填模型密钥或清空历史。Intel Mac 和 Windows 继续下载 0.1.4。

| 设备 | 版本与下载 | 安装文件 |
| --- | --- | --- |
| Apple Silicon Mac | [0.1.5](https://github.com/VectorHo/HtDot-Releases/releases/tag/v0.1.5) | 文件名包含 `macos-arm64` 的 `.dmg` |
| Intel Mac | [0.1.4](https://github.com/VectorHo/HtDot-Releases/releases/tag/v0.1.4) | 文件名包含 `macos-x64` 的 `.dmg` |
| Windows x64 | [0.1.4](https://github.com/VectorHo/HtDot-Releases/releases/tag/v0.1.4) | 文件名包含 `windows-x64` 的安装 `.exe` |

当前 latest feed 只提供 Apple Silicon 的 0.1.5。旧 Intel/Windows 客户端遇到缺目标平台的 feed 可能显示检查失败，不会安装错误架构的包；原 0.1.4 下载保留。0.1.5 起客户端将缺目标解释为该平台没有更新。启动 30 秒后检查，此后每 6 小时检查；发现新版提示，下载、安装和重启仍由用户确认。

本版本先用于开发和 OTA 验收。构建、签名、公开下载与实机验收分别记录；Intel Mac 和 Windows 实机验收尚未完成。GitHub latest 用于客户端发现更新，不表示三平台正式验收通过。

macOS 安装包经过 Developer ID 签名和 Apple 公证。Windows 安装包未做 Authenticode，系统可能显示未知发布者。所有 OTA 包都有绑定版本的 Tauri updater 签名。

## 历史错误提醒

模型恢复后，旧失败记录仍保留原始结果。0.1.4 起，在 **动态 → 需要处理** 点击 **已查看，不再提醒** 可关闭已核对的失败或中断提醒；重启后保持。记录保留在“已结束／全部动态”，可点击“恢复提醒”。待审批、活动或结果未知的工具仍需先处理，不能直接关闭。后续对话成功不会自动确认旧任务。

## 应用内更新

已安装发行版时，打开 **设置 → 模型与本地服务 → 应用更新 → 检查更新 → 安装更新并重启**。先完成活动任务、处理待审批，再安装。更新会验证签名、备份 SQLite，并在重启后核对完整应用和本地工作区。

客户端使用：

```text
https://github.com/VectorHo/HtDot-Releases/releases/latest/download/latest.json
```

无需 GitHub 登录。离线或更新源不可用时，本地工作仍可继续。HtDot Verify 是隔离测试包，不连接此更新源。不要把 `.sig` 或 OTA `.tar.gz` 当作普通安装文件。

OTA 管理页面后续属于独立云协同 Web 项目。目前 GitHub 直接承担文件分发；以后通过过渡客户端迁移地址并保留旧源兼容，无需等待云端页面才使用更新。

## English

[v0.1.5](https://github.com/VectorHo/HtDot-Releases/releases/tag/v0.1.5) is a **development test release for Apple Silicon Mac only**. It fixes incomplete chat-history responses in the desktop transport. A successful model connection test does not exercise that response path. This repair does not require a new API key or deletion of conversation history.

Apple Silicon users can install the signed, notarized DMG or use signed OTA. Intel Mac and Windows x64 downloads remain at [v0.1.4](https://github.com/VectorHo/HtDot-Releases/releases/tag/v0.1.4). The current latest feed contains only Apple Silicon. Older Intel/Windows clients may report a check failure because their target is absent; they will not install another architecture. Version 0.1.5 treats an absent target as no update for that platform.

Automatic checks run 30 seconds after startup and every 6 hours. Download, installation and restart require an explicit user action. macOS packages are signed and notarized. Windows 0.1.4 has no Authenticode signature. Every OTA package has a version-bound Tauri updater signature. Intel Mac and Windows device acceptance remain pending; GitHub latest does not imply production readiness.

In **Activity → Needs attention**, use **Reviewed · stop reminding** after reviewing a failed or interrupted run. The original result remains in Finished and All activity. **Restore reminder** reverses this choice. Reviews persist after restart. Pending approvals and uncertain tool results cannot be dismissed.

To update an installed release, open **Settings → Model and local service → Application updates → Check for updates → Install update and restart**. Resolve active work and pending approvals first. Updates verify signatures, back up SQLite and check the installed version after restart.

The public feed above requires no GitHub login. Local work remains available offline. Verify packages do not use this feed. A future independent cloud project will provide release administration and can replace the update source through a transition client release.
