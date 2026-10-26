# Changelog

> This file documents important changes in Vyku.
> Versioning follows [Semantic Versioning](https://semver.org/).
> Updated: 2026-10-25

[简体中文](CHANGELOG.md) | [繁體中文](CHANGELOG-zh-Hant.md)

---

## [0.18.0] - 2026-10-26


### 2026-10-25 Update

- **Migrated the visual system to Clay (replaces the V0.18.0-A blue + cool-gray baseline)**
- Brand color moved from blue `#2563EB` to clay `#D97757`; the canvas is now warm paper `#FAF9F5` and primary text is graphite `#141413` (no pure white or pure black)
- Primitive layer renamed to Clay tokens: `clay` / `clayDark` / `clayPress` / `clayDeep` / `clayTint` / `neutral50…900` (including the calibrated 450 step) / `slate` / `ivory` / `darkCanvas`, plus the four functional states (solid / bg / text / border) and the dark neutral ramp
- The 16 semantic tokens keep their **field names**; only the light and dark values changed. Three contrast calibrations: filled-button text now graphite (5.90:1), clay used as text or icon now takes the deeper `clayPress` (5.68:1), and tertiary text moves to `#6E6D66` (4.93:1)
- Three font families: Noto Serif SC for headings (`GoogleFonts.notoSerifSc`, weight capped at 600, never 700), Noto Sans SC for body text, and JetBrains Mono for eyebrows and numeric labels; all 15 Material roles now follow Clay `font.scale`
- Component layer: cards use surface steps plus a 1px hairline with `elevation` 0; `ColorScheme.surfaceTint` is cleared so surfaces are no longer tinted by the primary color; outlined buttons use ink, text buttons use the deeper clay, and the enabled input border uses tertiary text to reach 3:1
- Spacing and radius now cover the Clay steps (`space3/7/8/9/10`, `radiusXl/2xl`), while the touch target stays at 48 (stricter than Clay's 44)
- Added contrast assertion tests across 16 tokens × light/dark (4.5:1 for text, 3:1 for non-text, with the WCAG relative-luminance algorithm and five pinned known deviations); `lib/` no longer contains legacy color names, `Colors.white` / `Colors.black`, or hardcoded colors outside the primitive layer
- Known deviations are recorded in spec 4.5.1 (D1–D4 accepted, D6 an intentional line-height deviation); the former open decision **D5 is resolved** — all 8 code sites for page section titles now use `ring` instead of raw clay (5.68:1 on the canvas, 5.35:1 in dark)
- Fixed input focus-state contrast: `inputDecorationTheme` now resolves label and floating-label colors per state (focused `ring` at 5.39:1, error `error`, otherwise `textSecondary`), and a new `textSelectionTheme` gives the cursor and handles `ring` with a `ring@40%` selection; the focused label moves from the framework default of raw clay at 2.81:1 to 5.39:1, backed by render-level assertions and pins for the D5 sites

### 2026-10-18 Update

- **Client visual system (V0.18.0-A, complete)**
- Established three layers of visual tokens: primitive values (`AppColors`, `AppSizes`, `AppSpacing`, `AppShadows`, `AppMotion`), semantics (16 semantic colors, one set each for light and dark, wired into `ColorScheme`), and components (theme mappings for buttons, inputs, cards, lists, dialogs, navigation bars, chips, snack bars, app bars, and progress indicators)
- Added a type scale with a Chinese font-family fallback strategy; statistics, amounts, and dates use tabular figures so digit changes no longer shift layout
- Added responsive breakpoints with `compact` / `medium` / `expanded` layouts and an 840 cap on content width on wide screens
- Added System / Light / Dark themes, with a theme entry and selection subpage under Settings → Language & Display, and the choice is kept across restarts
- Redesigned seven page types: asset list, search, asset detail, create/edit, reminders, attachments, and settings
- Unified focus-ring and disabled-state visuals, with visible keyboard focus
- Dark theme now expresses hierarchy with borders and surface brightness instead of shadows
- Added new copy keys such as `settingsTheme*` and `homeReminderFuture`, keeping Simplified Chinese, Traditional Chinese, and English complete
- Added token compliance scanning, so pages no longer contain hardcoded colors, `Colors.*`, `withOpacity`, or font-size literals

---

## [0.14.1] - 2026-07-20

### 2026-07-20 Update

- Limited backup file size, ZIP entry count, declared uncompressed size, and compression ratio to reduce memory-exhaustion risks from unsafe backups
- **Signed Android release and cross-platform data safety**
- Added field-specific Android controls for numbers, dates, selects, switches, and multiline text, with first-error focusing
- Added camera, image, and file attachment sources with SHA-256 verification before and after storage and cleanup on failure
- Added contextual notification permission requests and rescheduling of pending reminders after permission recovery
- Unified Windows and Android on the encrypted schema 3 backup format, with database and attachment validation plus safe rollback
- Established schema 3 as the first public backup compatibility baseline; unpublished schema 1 / 2 test backups are not supported
- Opened Android data tools in Settings and added 24-hour automatic update checks plus manual checks
- Limited update checks to the public GitHub latest release and accepted only trusted repository HTTPS download links
- Switched Android public builds to a fixed release signature; V0.13.0 debug builds cannot upgrade to the signed package, while higher versions using the V0.14.1 signing identity can upgrade in place

---

## [0.13.0] - 2026-07-15

### 2026-07-15 Update

- **Android MVP**
- Added the Android platform project and three-entry navigation for Assets, Reminders, and Settings
- Completed asset create, view, edit, delete, search and filters, plus reminder-to-asset navigation
- Added in-app image preview and Android system-app opening for PDFs and documents
- Stored data in the current device's app-private directory and disabled Android Auto Backup
- Completed Simplified Chinese, Traditional Chinese, and English support and passed offline cold-start acceptance
- This release does not include cross-device sync, complete Android backup and restore, or the complete system-notification experience

---

## [0.12.0] - 2026-07-05

### 2026-07-05 Update

- **Multi-platform UI/UX baseline**
- Added lightweight spacing rules to align page padding, cards, and state components
- Unified the core task-flow skeleton across Home, Search, Asset Detail, Create, Edit, Reminders, and Settings
- Added required-field validation for asset forms, field-level errors, and discard confirmation for unsaved changes
- Improved the Home reminder entry with overdue, due-soon, and pending states, plus asset-detail navigation
- Grouped Settings by Language & Display, Data & Backup, Import & Export, and Version & About
- Added V0.12.0 trilingual copy completeness tests for Simplified Chinese, Traditional Chinese, and English

---

## [0.11.0] - 2026-07-05

### 2026-07-05 Update

- **Data safety and restore**
- Added `.vbk` backup verification for password, integrity, schema, and database-file checks before restore
- Added pre-restore backup summaries and overwrite warnings, with automatic rollback when restore fails
- Added attachment health checks for missing files, hash mismatches, and orphan files
- Clarified that plain CSV / JSON exports do not include attachments and are not full backups
- Completed related Simplified Chinese, Traditional Chinese, and English copy

---

## [0.10.0] - 2026-07-02

### 2026-07-02 Update

- **Windows productization improvements**
- Added a `portable` / `installer` data path service: portable uses `<app directory>/data`, installer uses the system application documents directory, and migration uses encrypted backups
- Added pending reminders to the home screen while keeping the asset dashboard, category entry points, and recent updates
- Improved batch import with explicit flow states, overwrite counts, duplicate-title skipping within one file, and free-tier import limits
- Added Data & Backup, data path, migration guidance, and light free-tier prompts to Settings
- Completed related Simplified Chinese, Traditional Chinese, and English copy

---

## [0.9.0] - 2026-06-30

### 2026-07-01 Update

- **Pre-release testing fixes**
- Fixed a Windows startup issue where the app could stay in the background without showing a window when old reminder data existed
- Localized asset subcategories, template names, and template fields across the three supported languages
- Renamed the home “Asset Stats” section to “Asset Dashboard” and fixed the asset category order
- Simplified the CSV import template to make importing easier
- Added regression tests for import templates, template localization, and reminder rescheduling
- Added the `release-notes/` directory to archive the trilingual GitHub Releases notes

### 2026-06-30 Update

- **Documentation rules synchronized**
- Git commit convention now uses Chinese commit types such as `功能`, `修复`, and `文档`; historical English-type commits are kept as-is
- Release process now requires GitHub Release notes in Simplified Chinese, Traditional Chinese, and English
- Release package names now follow `vyku-v<version>-<platform>-<arch>-<package-type>.<ext>`; package type must be `installer` or `portable`
- README version badges updated to 0.9.0, with release-page language notes synchronized

- **V0.9.0 fully implemented — 6 features**
- Template optimization: 9 new sub-templates (Phone/Computer/Camera/Appliance/Web Account/Game Account/Software Account/Contract/Invoice), template picker grouped by category
- Subscription improvement: Added start_date/end_date fields, detail page shows period and countdown
- Reminder enhancement: Hour/minute time picker, precise trigger time display, improved formatTriggerTime
- Home dashboard: Stats cards, category filter chips, empty-state guidance, list items show update time
- Search refactoring: Multi-field fuzzy search (title/subtitle/custom fields/owner/location), category filter dropdown, enhanced search history
- Batch import: CSV template generator, preview first 5 rows, 3 conflict strategies (skip/overwrite/create), import result statistics

---

## [0.8.0] - 2026-06-27

### 2026-06-29 Update

- **Self-testing fixes completed**
- Unified app name per locale (Simplified Chinese: Vyku归屿, Traditional Chinese: Vyku歸嶼, English: Vyku)
- Fixed i18n bug in Backup & Restore screen (Traditional Chinese/English no longer show Simplified Chinese)
- Renamed "VPS/Server" template to "Server"
- Added DatePicker for all date-type template fields (tap to select date)
- Unified global font to Noto Sans SC

### Self-Testing Release

- Entering self-testing phase
- Goal: Enter 50 real assets, validate complete workflow
- Cover devices, domains, subscriptions, contracts, certificates

---

## [0.7.0] - 2026-06-27

### 2026-06-27 Update

- **V0 fully completed**
- All 17 tasks implemented
- 18 unit tests passing
- Code review security issues fixed

### Features Completed

- Database: 7 tables, 4 DAOs
- Templates: 7 built-in templates
- UI: Home, Create, Detail, Edit, Search, Settings
- Attachments: File upload, preview, vault storage
- Reminders: CRUD, notification scheduling, recurring reminders
- Backup: AES-256-GCM encryption, HMAC integrity verification
- Import/Export: CSV/JSON formats
- i18n: Simplified Chinese, Traditional Chinese, English

## [0.1.0] - 2026-06-25

### 2026-06-26 Update

- Flutter 3.44.4 + Dart 3.12.2
- Windows desktop development environment configured
- Visual Studio 2026 integration
- Task 1: Project initialization completed

### Initial Release

- Project initialization
- Completed product planning and documentation
- Technical architecture design completed
- Data model definition completed

### 2026-10-26 Update (V0.18.0-B: web site)

- Added the `site/` static website: **18 pages** (home, features, docs, download, changelog and FAQ across Simplified Chinese, Traditional Chinese and English); Simplified Chinese lives at the root with `zh-Hant/` and `en/` as subdirectories
- The site reuses the same **Clay design system** as the clients (warm paper `#FAF9F5`, clay accent `#D97757`, slate `#141413`, 11 warm neutrals); tokens and components are byte-identical copies of `clay-html` v0.14.0, with only container spacing and CJK serif stacks overridden
- Layout follows a 12-column grid across four breakpoints (375 / 768 / 1024 / 1440) with editorial typography (serif headings, monospace eyebrows, `tabular-nums`); hierarchy relies on surface steps and 1px hairlines — no shadows, gradients or external links anywhere
- Download entries follow **truthfulness first**: until V0.18.0 ships, both platform buttons are disabled placeholders with three-language explanations, and no link points to `.apk`, `.zip` or `.exe`
- Added author-side tooling: `tools/build_site.py` (zero-runtime static generator with `--check`) and `tools/check_site.py` (gates for forbidden patterns, links, i18n structure, accessibility, size, contrast and canvas colour)
- All site gates pass: 25 contrast pairs within tolerance, 12 forbidden patterns at 0 hits, 0 broken/external/binary links, byte-identical regeneration, no horizontal scrolling in 32/32 width combinations, canvas mode colour exactly `#FAF9F5` / `#1F1E1D`
- Fixed three layout defects found by manual inspection: an unhidden icon sprite causing ~170px of blank space above the fold, misaligned FAQ chevrons, and a `34em` list cap squeezing the capability list into a narrow strip
