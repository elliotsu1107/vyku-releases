# 归屿 Vyku

> 让家庭的重要资产都有归处
> 更新日期：2026-07-19

[![Version](https://img.shields.io/badge/version-0.14.0-green.svg)](CHANGELOG.md)

---

## 简介

归屿是一个家庭数字资产中枢，帮助你统一管理家庭的重要资产、附件、关系和提醒。

**本地优先** - 你的数据永远在你手中，不依赖任何云服务。

---

## 功能特性

- **资产管理** - 统一管理设备、账号、订阅、域名、服务器、证件、文件
- **附件管理** - 支持拍照、选择图片和文件，校验后保存到应用私有目录
- **到期提醒** - 保修、域名、订阅到期自动提醒，并支持 Android 通知权限恢复
- **本地搜索** - 快速查找任何资产
- **加密备份** - AES-256-GCM 加密，安全导出导入
- **备份验证与恢复保护** - 恢复前验证备份包，失败时自动回滚
- **附件健康检查** - 检查附件缺失、hash 异常和孤儿文件
- **CSV/JSON 导入导出** - 明文数据交换
- **数据目录说明** - 区分便携版和安装版数据路径，通过备份包互导
- **跨平台恢复** - Windows 与 Android 使用统一 schema 3 加密备份格式
- **版本检查** - 自动或手动检查公开 GitHub 稳定版本
- **轻量免费版** - 基础流程可用，重度规模和效率能力会提示升级
- **三语支持** - 简体中文、繁體中文、English

---

## 支持的资产类型

| 类型 | 示例 |
|---|---|
| 实体资产 | 手机、电脑、NAS、相机、家电 |
| 数字资产 | 账号、订阅服务、域名、VPS/服务器 |
| 文件资产 | 证件、合同、发票、保修单、保险 |

---

## 技术栈

- **框架**: Flutter 3.44.4
- **数据库**: SQLite + Drift
- **平台**: Windows、Android

---

## 下载安装

访问 [GitHub Releases](https://github.com/elliotsu1107/vyku-releases/releases) 下载最新版本。

**Windows**: 下载最新 `vyku-v<version>-windows-x64-portable.zip`，解压后运行 `vyku.exe`

发布包命名示例：`vyku-v0.14.0-windows-x64-portable.zip`。安装包标注 `installer`，便携包标注 `portable`。

**Android**: 下载 `vyku-v0.14.0-android.apk` 和同名 `.sha256` 文件。安装前核对 APK 的 SHA-256；从浏览器或文件管理器安装时，仅临时允许“安装未知应用”，完成后恢复该来源的禁止安装设置。

发布页说明提供简体中文、繁體中文、English 三语。

### Android 升级说明

- V0.13.0 是内部 debug 签名包，不能覆盖安装 V0.14.0 正式包；请将 V0.14.0 视为全新安装。
- 从 V0.14.0 起，使用同一正式签名且 `versionCode` 更高的版本可以覆盖升级。
- 卸载应用会删除 Android 应用私有目录。迁移或重装前先创建加密 `.vbk` 备份。

### 备份兼容性

V0.14.0 的 schema 3 是首个公开备份兼容基线，包含数据库、活跃附件清单、大小和 SHA-256。Windows 与 Android 可通过 `.vbk` 双向迁移；未公开的 schema 1 / 2 测试备份不受支持。

更新检查只访问公开的 [GitHub latest release API](https://api.github.com/repos/elliotsu1107/vyku-releases/releases/latest)，不上传设备、资产或使用数据。

---

## 数据目录

| 版本形态 | 数据位置 | 说明 |
|---|---|---|
| 便携版 portable | `<程序目录>/data` | 发布包内包含 `portable.flag`，解压后数据会跟随整个文件夹移动 |
| 安装版 installer | 系统应用文档目录，Windows 通常为 `%USERPROFILE%/Documents` | 实际路径以设置页展示为准 |

数据库文件为 `vyku.sqlite`，附件位于 `vault/assets/`。便携版和安装版不要手动混用数据库文件，迁移请使用加密备份包。

---

## 文档

- 产品文档 - 内部开发文档，不随公开仓库发布
- [更新日志](CHANGELOG.md) - 版本更新说明
- [Release Notes](release-notes/) - GitHub Releases 发布说明归档

---

## 联系方式

- Issues: [GitHub Issues](https://github.com/elliotsu1107/vyku/issues)
