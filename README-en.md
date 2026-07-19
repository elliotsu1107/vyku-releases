# Vyku

> Every important asset, a place to belong
> Updated: 2026-07-19

[![Version](https://img.shields.io/badge/version-0.14.0-green.svg)](CHANGELOG-en.md)

---

## About

Vyku is a family digital asset hub that helps you manage all your important assets, attachments, relationships, and reminders in one place.

**Local-first** - Your data stays with you, no cloud dependency required.

---

## Features

- **Asset Management** - Manage devices, accounts, subscriptions, domains, servers, certificates, and documents
- **Attachment Management** - Capture photos or choose images and files, then validate and store them in the app-private directory
- **Reminders** - Automatic reminders for warranties, domains, and subscriptions, including Android notification-permission recovery
- **Local Search** - Quickly find any asset
- **Encrypted Backup** - AES-256-GCM encryption for secure export/import
- **Backup Verification & Restore Protection** - Verify backups before restore, with automatic rollback on failure
- **Attachment Health Check** - Detect missing files, hash mismatches, and orphan files
- **Data Directory Clarity** - Separate portable and installer data paths, with backup-based migration
- **Cross-platform Restore** - Windows and Android share the encrypted schema 3 backup format
- **Update Checks** - Automatically or manually check public stable GitHub releases
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
- **Platforms**: Windows and Android

---

## Download & Install

Visit [GitHub Releases](https://github.com/elliotsu1107/vyku-releases/releases) to download the latest version.

**Windows**: Download the latest `vyku-v<version>-windows-x64-portable.zip`, extract it, and run `vyku.exe`.

Package name example: `vyku-v0.14.0-windows-x64-portable.zip`. Installers use `installer`; portable packages use `portable`.

**Android**: Download `vyku-v0.14.0-android.apk` and its matching `.sha256` file. Verify the APK SHA-256 before installation. When installing from a browser or file manager, allow “Install unknown apps” only temporarily and disable it for that source afterward.

Release notes are provided in Simplified Chinese, Traditional Chinese, and English.

### Android Upgrade Notes

- V0.13.0 used an internal debug signature and cannot be upgraded in place to the signed V0.14.0 package. Treat V0.14.0 as a fresh install.
- Starting with V0.14.0, later builds signed with the same release key and a higher `versionCode` can upgrade in place.
- Uninstalling removes the Android app-private directory. Create an encrypted `.vbk` backup before migration or reinstallation.

### Backup Compatibility

Schema 3 in V0.14.0 is the first public backup compatibility baseline. It includes the database plus active-attachment manifests, sizes, and SHA-256 values. `.vbk` backups can move between Windows and Android; unpublished schema 1 / 2 test backups are not supported.

To prevent memory exhaustion on mobile devices, an encrypted backup file is limited to 65 MB. A ZIP may contain at most 256 entries, declare at most 64 MB of uncompressed data, and use no more than a 1000:1 compression ratio per entry. Backups over these limits are rejected before entry content is read.

Update checks only access the public [GitHub latest release API](https://api.github.com/repos/elliotsu1107/vyku-releases/releases/latest). No device, asset, or usage data is uploaded.

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
