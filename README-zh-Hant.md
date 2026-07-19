# 歸嶼 Vyku

> 讓家庭的重要資產都有歸處
> 更新日期：2026-07-19

[![Version](https://img.shields.io/badge/version-0.14.0-green.svg)](CHANGELOG-zh-Hant.md)

---

## 簡介

歸嶼是一個家庭數位資產中樞，幫助你統一管理家庭的重要資產、附件、關係和提醒。

**本地優先** - 你的數據永遠在你手中，不依賴任何雲端服務。

---

## 功能特性

- **資產管理** - 統一管理設備、帳號、訂閱、網域、伺服器、證件、文件
- **附件管理** - 支援拍照、選擇圖片和檔案，驗證後儲存到應用程式私有目錄
- **到期提醒** - 保固、網域、訂閱到期自動提醒，並支援 Android 通知權限恢復
- **本地搜尋** - 快速查找任何資產
- **加密備份** - AES-256-GCM 加密，安全匯出匯入
- **備份驗證與恢復保護** - 恢復前驗證備份包，失敗時自動回滾
- **附件健康檢查** - 檢查附件缺失、hash 異常和孤兒檔案
- **資料目錄說明** - 區分便攜版和安裝版資料路徑，透過備份包互導
- **跨平台恢復** - Windows 與 Android 使用統一 schema 3 加密備份格式
- **版本檢查** - 自動或手動檢查公開 GitHub 穩定版本
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
- **平台**: Windows、Android

---

## 下載安裝

訪問 [GitHub Releases](https://github.com/elliotsu1107/vyku-releases/releases) 下載最新版本。

**Windows**: 下載最新 `vyku-v<version>-windows-x64-portable.zip`，解壓後執行 `vyku.exe`

發布包命名示例：`vyku-v0.14.0-windows-x64-portable.zip`。安裝包標註 `installer`，便攜包標註 `portable`。

**Android**: 下載 `vyku-v0.14.0-android.apk` 和同名 `.sha256` 檔案。安裝前核對 APK 的 SHA-256；從瀏覽器或檔案管理器安裝時，只暫時允許「安裝未知應用程式」，完成後恢復該來源的禁止安裝設定。

發布頁說明提供簡體中文、繁體中文、English 三語。

### Android 升級說明

- V0.13.0 是內部 debug 簽名包，不能覆蓋安裝 V0.14.0 正式包；請將 V0.14.0 視為全新安裝。
- 從 V0.14.0 起，使用同一正式簽名且 `versionCode` 較高的版本可以覆蓋升級。
- 解除安裝應用程式會刪除 Android 應用程式私有目錄。移轉或重新安裝前先建立加密 `.vbk` 備份。

### 備份相容性

V0.14.0 的 schema 3 是第一個公開備份相容基線，包含資料庫、有效附件清單、大小和 SHA-256。Windows 與 Android 可透過 `.vbk` 雙向移轉；未公開的 schema 1 / 2 測試備份不受支援。

為避免行動裝置記憶體耗盡，單一加密備份檔案最大 65 MB；ZIP 最多 256 個項目，宣告解壓縮總量最大 64 MB，單一項目壓縮率不得超過 1000 倍。超出限制的備份會在讀取項目內容前被拒絕。

更新檢查只會存取公開的 [GitHub latest release API](https://api.github.com/repos/elliotsu1107/vyku-releases/releases/latest)，不會上傳裝置、資產或使用資料。

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
