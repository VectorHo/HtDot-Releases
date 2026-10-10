# HtDot desktop releases / 桌面发行仓库

这个仓库用于分发 HtDot 的 macOS、Windows 安装包和签名 OTA 更新。应用源码保存在独立的 HtDot 开发仓库。

## 当前状态

目前没有公开正式版本。候选包先保存在 GitHub Release 草稿中，仅有仓库权限的维护者可见；因此公开的 Releases 页面可能为空。这不代表仓库未使用。维护者正在验收 0.1.2，其中包含后续界面优化与桌面连接修复。

候选包构建、签名、实机安装和真实 OTA 是不同的验收步骤。通过构建不代表可以公开发布。Windows 和 Intel Mac 的实机验收仍待具备对应设备后完成。

## 下载与更新

正式版本发布后，从 [Releases](https://github.com/VectorHo/HtDot-Releases/releases) 下载与设备匹配的安装包。macOS 分 Apple Silicon 与 Intel；Windows 为 x64。

客户端内置更新地址：

```text
https://github.com/VectorHo/HtDot-Releases/releases/latest/download/latest.json
```

发布前该地址可能返回 404，客户端仍可本地工作。更新文件、版本清单和许可证随对应版本一起分发。OTA 管理 Web 页面以后在独立云协同项目实现，不是本地运行或下载的前置条件。

macOS 安装包经过 Developer ID 签名和 Apple 公证。Windows 安装包允许不做 Authenticode；所有平台的 OTA 包都必须带有绑定版本的 Tauri updater 签名。

## English

This repository distributes HtDot desktop installers, licenses, and signed OTA feeds. It does not contain application source code.

No public production release is available yet. Release drafts are visible only to authorized maintainers. An empty public Releases page does not mean this repository is unused. Version 0.1.2 is undergoing acceptance.

After publication, download the package for your platform from Releases. The client uses the `latest.json` URL above. Before publication, that endpoint can return 404; local work remains available. A future cloud administration UI is not required for local use or downloads.

macOS packages require Developer ID signing and Apple notarization. Windows installers may have no Authenticode signature. Every OTA package requires a version-bound Tauri updater signature. Device and upgrade acceptance remain separate from CI build results.
