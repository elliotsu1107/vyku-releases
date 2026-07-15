# Vyku

> Every important asset, a place to belong

[![Version](https://img.shields.io/badge/version-0.13.0-green.svg)](CHANGELOG-en.md)

---

## About

Vyku is a family digital asset hub that helps you manage all your important assets, attachments, relationships, and reminders in one place.

**Local-first** - Your data stays with you, no cloud dependency required.

---

## Features

- **Asset Management** - Manage devices, accounts, subscriptions, domains, servers, certificates, and documents
- **Attachment Management** - Upload images, PDFs, and documents, linked to assets
- **Reminders** - Automatic reminders for warranties, domains, and subscriptions
- **Local Search** - Quickly find any asset
- **Encrypted Backup** - AES-256-GCM encryption for secure export/import
- **Backup Verification & Restore Protection** - Verify backups before restore, with automatic rollback on failure
- **Attachment Health Check** - Detect missing files, hash mismatches, and orphan files
- **Data Directory Clarity** - Separate portable and installer data paths, with backup-based migration
- **Light Free Tier** - Core workflows stay usable, heavy scale and efficiency features show upgrade prompts
- **Multi-language** - Simplified Chinese, Traditional Chinese, English

---

## Supported Asset Types

| Type | Examples |
|---|---|
| Physical Assets | Phones, computers, NAS, cameras, appliances |
| Digital Assets | Accounts, subscriptions, domains, VPS/servers |
| Document Assets | Certificates, contracts, invoices, warranties, insurance |

---

## Tech Stack

- **Framework**: Flutter
- **Database**: SQLite + Drift
- **Platform**: Windows available now, Android MVP internally validated, iOS planned

---

## Download & Install

Visit [GitHub Releases](https://github.com/elliotsu1107/vyku-releases/releases) to download the latest version.

**Windows**: Download the latest `vyku-v<version>-windows-x64-portable.zip`, extract it, and run `vyku.exe`.

Package name example: `vyku-v0.13.0-windows-x64-portable.zip`. Installers use `installer`; portable packages use `portable`.

**Android**: The current source can build and install a debug APK for Android MVP internal testing. A signed public package is not available yet.

Release notes are provided in Simplified Chinese, Traditional Chinese, and English.

### Android MVP Scope

Android supports creating, viewing, editing, and deleting assets, search and filters, reminder viewing, and attachment opening. Data stays in the app-private directory on the current device and is removed when the app is uninstalled.

This release does not include cross-device sync, complete Android backup and restore, or the complete system-notification experience.

---

## Data Directory

| Package type | Data location | Notes |
|---|---|---|
| Portable | `<app directory>/data` | Portable packages include `portable.flag`, so data moves with the extracted folder |
| Installer | System application documents directory, usually `%USERPROFILE%/Documents` on Windows | The actual path is shown in Settings |

The database file is `vyku.sqlite`, and attachments live under `vault/assets/`. Do not manually mix portable and installer database files. Use encrypted backups for migration.

---

## Documentation

- Product docs - Internal development documents, not published with the public repository
- [Changelog](CHANGELOG-en.md) - Version update notes
- [Release Notes](release-notes/) - Archived GitHub Releases notes

---

## Contact

- Website: [vyku.app](https://vyku.app)
- Issues: [GitHub Issues](https://github.com/elliotsu1107/vyku/issues)
