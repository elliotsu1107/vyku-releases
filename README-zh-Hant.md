# 歸嶼 Vyku

> 讓家庭的重要資產都有歸處

[![Version](https://img.shields.io/badge/version-0.13.0-green.svg)](CHANGELOG-zh-Hant.md)

---

## 簡介

歸嶼是一個家庭數位資產中樞，幫助你統一管理家庭的重要資產、附件、關係和提醒。

**本地優先** - 你的數據永遠在你手中，不依賴任何雲端服務。

---

## 功能特性

- **資產管理** - 統一管理設備、帳號、訂閱、網域、伺服器、證件、文件
- **附件管理** - 上傳圖片、PDF、文件，與資產關聯
- **到期提醒** - 保固、網域、訂閱到期自動提醒
- **本地搜尋** - 快速查找任何資產
- **加密備份** - AES-256-GCM 加密，安全匯出匯入
- **備份驗證與恢復保護** - 恢復前驗證備份包，失敗時自動回滾
- **附件健康檢查** - 檢查附件缺失、hash 異常和孤兒檔案
- **資料目錄說明** - 區分便攜版和安裝版資料路徑，透過備份包互導
- **輕量免費版** - 基礎流程可用，重度規模和效率能力會提示升級
- **三語支援** - 簡體中文、繁體中文、English

---

## 支援的資產類型

| 類型 | 範例 |
|---|---|
| 實體資產 | 手機、電腦、NAS、相機、家電 |
| 數位資產 | 帳號、訂閱服務、網域、VPS/伺服器 |
| 文件資產 | 證件、合約、發票、保固單、保險 |

---

## 技術棧

- **框架**: Flutter
- **資料庫**: SQLite + Drift
- **平台**: Windows 目前可用，Android MVP 已完成內部驗收，iOS 規劃中

---

## 下載安裝

訪問 [GitHub Releases](https://github.com/elliotsu1107/vyku-releases/releases) 下載最新版本。

**Windows**: 下載最新 `vyku-v<version>-windows-x64-portable.zip`，解壓後執行 `vyku.exe`

發布包命名示例：`vyku-v0.13.0-windows-x64-portable.zip`。安裝包標註 `installer`，便攜包標註 `portable`。

**Android**: 目前原始碼可建置並安裝 debug APK，用於 Android MVP 內部測試；暫不提供正式簽名安裝包。

發布頁說明提供簡體中文、繁體中文、English 三語。

### Android MVP 範圍

Android 端已支援資產新增、查看、編輯、刪除、搜尋篩選、提醒查看和附件開啟。資料僅儲存在目前裝置的應用程式私有目錄，解除安裝應用程式會清除資料。

本版本不包含跨端同步、Android 完整備份恢復和系統通知完整體驗。

---

## 資料目錄

| 版本形態 | 資料位置 | 說明 |
|---|---|---|
| 便攜版 portable | `<程式目錄>/data` | 發布包內包含 `portable.flag`，解壓後資料會跟隨整個資料夾移動 |
| 安裝版 installer | 系統應用文件目錄，Windows 通常為 `%USERPROFILE%/Documents` | 實際路徑以設定頁展示為準 |

資料庫檔案為 `vyku.sqlite`，附件位於 `vault/assets/`。便攜版和安裝版不要手動混用資料庫檔案，遷移請使用加密備份包。

---

## 文件

- 產品文件 - 內部開發文件，不隨公開倉庫發布
- [更新日誌](CHANGELOG-zh-Hant.md) - 版本更新說明
- [Release Notes](release-notes/) - GitHub Releases 發布說明歸檔

---

## 聯絡方式

- 官網: [vyku.app](https://vyku.app)
- Issues: [GitHub Issues](https://github.com/elliotsu1107/vyku/issues)
