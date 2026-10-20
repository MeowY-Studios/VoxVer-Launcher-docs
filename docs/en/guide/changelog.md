---
title: "Changelog"
---

# Changelog

This document records the feature changes, bug fixes and future plans for each version of VoxVer Launcher.

---

## v0.7.4 - 2026-10-21

> **Theme: Multi-Account Card Stack & Loader Adapter Architecture**

### ✨ New

- **Multi-Account Card Stack** — The accounts page is rebuilt as a card-stack style multi-account manager: multiple Microsoft accounts coexist, quick switching, and 3D skin preview (SkinViewer3D); new standalone `MicrosoftLoginModal` login dialog
- **Four-Loader Adapter Architecture** — Unified adapter layer for Forge / NeoForge / Fabric / Quilt (`BaseLoaderAdapter` + per-loader implementations); modloader service modularized

### ⚠️ Changes

- **Instance Module Temporarily Disabled** — The instances page now shows a "Not Available Yet" placeholder and related tests are rewritten; existing instance data is unaffected and the module will return in a future release

### ✨ Improvements

- **Stronger Dark Theme Presence** — Shadows replaced with brand-blue glow (sm / md / lg / xl); glass surfaces brightened (sidebar L=14→18, content 15→19, overlays 21→24); hover overlay 5%→8%, active 8%→12%; card inner highlights and title-bar glow now theme tokens, adapting to both light and dark themes
- **Homepage Hero Card** — Removed the welcome title and background to avoid abrupt color blocks in light/dark modes
- **i18n Copy Alignment** — zh-CN / en-US locale keys completed and updated

### 🏗 Engineering

- Added `electron/utils/version-meta.ts`, `electron/services/i18n.mod.service.ts`, and the `scripts/diagnose.mjs` diagnostic script
- gh CLI integrated into the release flow

---

## v0.7.3 Quality Fixes Batch - 2026-10-11

> **Theme: Quality Fixes and Engineering Baseline Alignment**

### 🔧 Fixes

- **i18n relative time showing raw keys** — Filled in missing `time.*` locale keys and instance deletion confirm texts; UI no longer displays raw keys like `time.minutesAgo`
- **Chinese/English key mismatch** — Filled in ~58 en-US keys that only existed in zh-CN (common / version / instance / download / types groups); English UI no longer shows raw keys
- **share_history table schema conflict** — Removed the duplicate first-version CREATE TABLE statement, kept the schema matching actual written values with status CHECK constraint
- **Real tsc type errors** — Fixed self-referencing type assertions in game.ipc.ts causing `never` type narrowing and implicit any; added explicit `VersionManifest` interface
- **PxConfirmProps not importable** — Moved type out of `<script setup>` to a dedicated `PxConfirm.types.ts`
- **36 failing unit tests → 278/278 green** — Test setup initializes i18n, assertions aligned with real IPC contracts

### ✨ Improvements

- **Animation stylesheet slimmed down** — animations.scss reduced from 480 lines to ~90; removed 19 unused `@keyframes` groups and all unused utility classes; deduplicated `prefers-reduced-motion`
- **Dead style cleanup** — Removed styles without corresponding template elements, merged duplicate definitions
- **Redundant logic cleanup** — Removed empty watchers, duplicate null checks and duplicate store declarations in App.vue
- **Loader display semantics aligned** — vanilla display value unified with i18n loaderLabels

### 🏗 Engineering

- **tsc dual-config back to exit 0** — Extracted `.vue` shim from env.d.ts into a standalone `shims-vue.d.ts` global declaration, fixing ~25 TS2307 errors
- **Type baseline aligned** — `@types/node` upgraded to ^24, consistent with engines `node>=24`
- eslint environment fixed (installed missing `vue-eslint-parser`)

---

## v0.7.3 - 2026-09-26

> **Theme: Standalone Update Page and Reworked Update Experience**

### ✨ New Features

- **Standalone Update Page** — The "Check for Updates" button in Settings now navigates to a standalone full-screen update page (`/update`): draggable title bar with window controls, banner (Logo + version + status pill: checking / up to date / update available), GitHub Release notes rendered as Markdown (whitelist filtered), bottom action bar (check / download / cancel / install / GitHub Releases link)
- **Silk Water Ripple Banner** — New `SilkBackground` component: zero-dependency WebGL silk ripple animation for the banner, colors follow the theme accent
- **Cancel Download** — Update downloads can be cancelled anytime (`CancellationToken`), state resets immediately on cancel
- **Download Progress Details** — Progress bar shows transferred / total size and real-time speed (MB/s)

### 🔧 Fixes

- "Check for Updates" button in Settings not responding
- No feedback when already on the latest version (status pill now shows it clearly)
- No status feedback during download

### ✨ Improvements

- Dual-channel update check arbitration: GitHub API version comparison conclusion takes priority; falls back to API conclusion when `latest.yml` lags behind
- Update state is recoverable: leaving and re-entering the update page still allows continuing download or install
- `builder-util-runtime` pinned to 9.5.1 to match electron-updater's embedded copy, fixing cross-copy `CancellationToken` failure

---

## v0.7.2 - 2026-09-26

> **Theme: Dual-Channel Update Check and Better Feedback**

### ✨ New Features

- **Dual-Channel Update Check** — Update checking now uses the GitHub API version comparison channel, directly comparing the local version with the latest GitHub Release version; no longer depends on `latest.yml`. Once an update is found, electron-updater handles download / install

### 🔧 Fixes & Improvements

- **No-feedback fix for update check** — Every outcome now has visible feedback: "New version available" popup when an update exists, "Already up to date" popup when versions match, error details on failure; button gains a "Checking" disabled state with 12-second timeout auto-recovery
- **Startup auto-check improved** — The startup auto-check also uses the version comparison channel; results are recoverable when the Settings page mounts
- **Download timing guarantee** — If updater metadata is not ready when downloading, it re-checks automatically before downloading; when `latest.yml` lags, the API comparison conclusion is used
- Version detection also works in development mode

---

## v0.7.1 - 2026-09-26

> **Theme: Crash Analysis System + XMCL Launch Core + Lumin UI/UX Design System**

### 🩺 Crash Analysis System

- **Crash Report Parsing** — Automatically captures and parses crash reports when the game exits abnormally (10 crash signature categories)
- **Crash Analysis Page** — New standalone "Crash Analysis" page (`/crash-analysis`) with report history list, severity labels, exception types and stack details
- **Crash Panel** — Launch page crash panel shows error descriptions, possible causes and suggested solutions

### 🚀 Launch Core & Mod Ecosystem

- **XMCL Launch Core Integration** — Rewrote the launch flow based on the @xmcl/* toolchain, fixing 1.16 crashes and 1.20.1 Forge self-contained version launch issues
- **Automatic Java Selection** — Matches Java 8/11/17/21/25 by MC version; LWJGL 2 (≤1.17) uses `java.exe`, LWJGL 3 (1.18+) uses `javaw.exe`
- **ModLoader System** — Forge / NeoForge / Fabric / Quilt one-click install with mutual exclusion switching; OptiFine and Fabric API auto-match compatible versions; smart dynamic version naming
- **Mod Management** — CurseForge + Modrinth dual-source search/download, batch operations, compatibility checks with badges, sorting, icon caching, zip export
- **Download System** — Multi-source switching (BMCLAPI mirror) with timeout control, IPC real-time progress, global download progress panel, caching

### 🎨 Lumin UI/UX Design System Merge

- Modal dialogs (4 sizes + responsive), Toast notifications (4 states), Badge gradient variants, modal/overlay animation keyframes and transition utilities
- PxSelect component replaces native select dropdowns
- Global color tokenization (`--voxver-*` CSS variables), fixing many hardcoded colors in dark/light themes
- Unified 250ms fade transition for page switches

### 🧩 Instances & Multiplayer

- **Instance Management Enhancements** — Detects local versions and supports importing them as managed instances; automatic instance import
- **P2P Sharing & Multiplayer** — 6-digit share codes + WebRTC direct connection for instance sharing; Settings sidebar split into separate P2P / Multiplayer sections

### 🌍 i18n & Others

- **i18n System** — Fixed 560+ hardcoded Chinese texts, added ~300 locale keys across 33 files
- **Fixed blank About page in packaged builds** — The `@` character in i18n messages triggered `Invalid linked format`, unmounting the Settings component; fixed with literal escaping (zh & en)
- JVM arguments no longer deduplicated with Set, keeping all `--add-opens`; unified G1GC; classpath dedup fixes `Duplicate key`
- Game process log capture (`[Game-STDOUT]` / `[Game-STDERR]`), dump last 200 lines on abnormal exit
- GitHub links migrated to the MeowY-Studios organization; docs site moved to voxver.meow-studio.tech
- Electron 42 + better-sqlite3 12, GitHub Actions upgraded to Node.js 24
- Integrated @openai/codex-security pre-commit security scanning

---

## v0.7.0 - Development Stage (content shipped in v0.7.1)

> **Theme: Design System Completion + Component Library + Multiplayer Settings + Launch Enhancement**

### 🎨 Design System Completion

- **Component Library Complete** — Finished design system and component library, unified component type definitions, eliminated `any` types
- **Theme Variable Fixes** — Replaced all hardcoded colors with CSS variable tokens for correct dark/light mode switching
- **Theme Palette Optimization** — Reduced theme color palette gaps, left-aligned color picker

### ⚔️ Multiplayer Settings

- **Settings Page Multiplayer Entry** — Added "Multiplayer" sidebar entry in settings
- **P2P & Multiplayer Separation** — Separated P2P sharing and multiplayer settings into independent sections

### 🌐 Internationalization Completion

- **i18n Full Completion** — Fixed ~560+ hardcoded Chinese text occurrences, added ~300 locale keys across 33 files
- **P2P Sharing Improvements** — Fixed import config loss, cancel during transfer, unpack progress push, disk space check, English error messages

### 🚀 Launch Process Enhancement

- **Immediate Stop on Abort** — Clicking stop during launch no longer waits 90s timeout; aborts immediately during dependency download/diagnose/version parsing
- **Stop Detail Popup** — JVM exit non-zero now renders friendly error summary popup instead of just showing "stopped"
- **Fake JAR Precise Detection** — Improved corrupted file detection to prevent 0-byte HTML from being treated as valid libraries
- **Auto-fix Corrupted Files** — JVM exit automatically scans and lists corrupted JAR paths + sizes + reasons

### 📦 Download System Optimization

- **Multi-source Timeout Control** — Download supports multi-source auto-switching with timeout control
- **Global Progress Panel** — Global download progress panel UI optimization

---

## v0.6.4 - 2026-07-17

> **Theme: macOS System Adaptation & Account Management Optimization**

### 🍎 macOS System Adaptation

- **macOS Dual Architecture Build** — New ARM64 / x64 dual architecture build support, macOS users can now download DMG packages directly
- **CI/CD Upgrade** — GitHub Actions now auto-builds macOS DMG packages
- **Node.js 24 LTS** — Runtime adapted for macOS 26, ensuring compatibility

### 👤 Account Management Optimization

- **Add Account Flow Optimization** — Clicking the "Add Account" button now directly navigates to the "Game Accounts & Profiles" tab in the Settings page, replacing the standalone account management popup for a smoother experience

### 🔧 Build

- Version bumped to v0.6.4

---

## v0.6.2 - 2026-07-04

> **Theme: Design System Refactoring & Splash Screen Optimization**

### 🎨 Design System Refactoring

- **Design Token System** — New `tokens.scss` defining OLED dark base (`#0a0a0a` → `#0d0d0d` → `#141414` → `#1a1a1a` four-layer steps), Neubrutalism utility classes
- **Frosted Glass Effect** — Sidebar, main content area, and version info region uniformly apply `backdrop-filter: blur(8px)` + `color-mix` semi-transparent effect
- **Frost Layer Fix** — Moved `backdrop-filter` to `::before` pseudo-element to resolve text blur issue
- **HomePage Simplification** — Removed launch button and stats cards, Hero card now displays only Logo + guide text
- **Bento Grid Layout Fix** — Fixed card height stretching and empty column issues

### 🖥️ Splash Screen Optimization

- **Dynamic Version Loading** — Version number read from `package.json` and injected at build time via `transformIndexHtml`, showing current version in real-time on splash screen
- **Progress Bar Animation** — Progress bar runs uniformly over 4 seconds, then fades out over 0.8s via `transitionend` event — no more flicker
- **Logo Replacement** — Splash screen now displays Alogo.png instead of text title

### 🎨 UI Details

- **Settings Page** — Hidden scrollbar (Chrome / Safari / Firefox / IE full coverage)
- **Sidebar** — Hidden scrollbar; removed bottom version info
- **About Page** — Adapted frosted glass texture; replaced airLogo with Alogo
- **Color Picker** — Fixed frosted layer blocking clicks (`pointer-events: none`)
- **Theme Colors** — Removed blue gradient background from Hero card, now uses solid background color

### 🔧 Build

- **Version Injection** — Added `html-inject-version` plugin in `electron.vite.config.ts` for build-time version injection

---

## v0.6.1 - 2026-07-02

> **Theme: Launch Stability & Download Reliability Major Fixes**

### 🔧 Game Launch Fixes

| Fix | Impact |
|-----|--------|
| **JVM Argument Dedup Fix** | Remove `Set` dedup in `buildJvmArguments` to prevent `--add-opens` args loss causing `ClassNotFoundException` |
| **Version Parsing Fix** | `extractBaseVersion` regex anchored at start, prevents incorrectly extracting version numbers from modpack names (e.g., "Hello, New Steam Journey! V1.4.2") |
| **Classpath Dedup** | `buildClasspath` adds `[...new Set(cp)]` dedup, fixes `Duplicate key` errors from duplicate library declarations in version JSON |
| **GC Parameter Compatibility** | Remove CMS GC (removed in Java 14+), unified to G1GC, fixes `Unrecognized VM option 'UseConcMarkSweepGC'` |
| **Missing File State Handling** | Frontend correctly handles `needsFileDownload` state, shows confirmation dialog before calling `confirmDownloadAndLaunch` |
| **Launch Status Switch Fix** | `spawnProcess` no longer blocks waiting for process exit, switches to "Running" state 1.5 seconds after process starts, fixes launcher stuck on "Launching" |
| **Independent Game Process** | `spawn` option changed to `detached: true`, game runs in independent process group, closing launcher won't terminate the game |

### 📦 File Integrity Verification

- **Library File Size Check** — `checkMissingFiles`, `downloadMissingFiles` add file size verification, detects 0-byte empty files and size mismatched files
- **Asset File Size Check** — `downloadAssets`, `checkMissingFiles` asset checks add file size verification
- **Clean Corrupted Files Before Download** — Delete 0-byte or size-mismatched files before re-downloading

### 🌐 Download System Fixes

- **BMCLAPI Redirect Support** — `downloadFile` adds HTTP 301/302/303/307/308 redirect following (max 5 times), fixes 0-byte files caused by BMCLAPI mirror redirects
- **Post-Download Verification** — Verify file size is not 0 after download, empty files treated as download failure
- **0-Byte File Skip Fix** — `downloadFile` no longer skips existing 0-byte files
- **Asset Download Source Optimization** — Asset primary source changed to official Minecraft asset server (`resources.download.minecraft.net`, no rate limit), BMCLAPI as fallback, fixes 3300+ asset files returning 403 due to BMCLAPI rate limiting (10 requests per 60 seconds)
- **Parallel Download Fallback Support** — `parallelDownload` adds `fallbackUrl` support, auto-tries fallback source on primary failure

### 🎨 UI/UX Optimization

- **Custom Download Confirmation Dialog** — Replaced native `confirm()` with `PxModal` component, includes warning icon, message text, cancel/download-and-launch buttons
- **Dialog Internationalization** — Added `launch.missingFilesTitle`, `launch.missingFilesMessage`, `launch.missingFilesHint` i18n entries

### ☕ Java Management

- **Default Java Version Recommendation** — Default to Java 21 when version number cannot be parsed (adapts to modern Forge/NeoForge modpacks)

## v0.6.0 - 2026-06-28

> **Theme: UI Architecture Refactor & Theme System Enhancement**

### 🎨 UI Refactor

- **Settings Page Categorization** — Settings page split into multiple sub-pages by function category, improving navigation efficiency
- **Unified Controls** — Global UI controls use `.vox-*` class prefix (`.vox-btn`, `.vox-input`, `.vox-card`, etc.), unified style standards
- **Theme System Refactor** — Light/dark theme complete switching + background customization + theme color customization, providing a more refined visual experience

---

## v0.5.5 - 2026-06-25

> **Theme: Internationalization Improvement & UI Optimization**

### ✨ New Features

- **i18n Internationalization** — Settings page sidebar, downloads page sidebar, more page sidebar, home account area, launch button and other core UI components now support multi-language switching
- **Language Switch** — Users can switch between Simplified Chinese and English in settings, with real-time interface updates

### 🔧 TypeScript Type Fixes

- **IPC Return Types** — Complete TypeScript type definitions for all IPC channels, eliminating type warnings
- **electronAPI Interface** — Standardize preload-exposed API interfaces for better type safety
- **ModLoader Parameter Types** — Fix type definitions for ModLoader installation parameters

### 🎨 UI/UX Optimization

- **Top Navigation Bar Icon Alignment** — Fix alignment issues between navigation bar icons and text
- **Main Content Area Rendering** — Optimize layout and rendering performance of the main content area

### 🔧 ModLoader Installation Improvement

- **Forge Installation** — Improve Forge ModLoader installation process
- **NeoForge Installation** — Add complete NeoForge ModLoader installation support
- **Quilt Installation** — Improve Quilt ModLoader installation process
- **Fabric Installation** — Fix issues during Fabric installation

### 📝 Documentation Updates

- **Launcher Name Change** — Project officially renamed from "MC Launcher Alpha (MCLA)" to "VoxVer Launcher", code repository renamed from `MC-Launcher-Alpha` to `VoxVer-Launcher`, docs repository renamed from `MC-Launcher-Alpha-docs` to `VoxVer-Launcher-docs`, all related documentation updated accordingly
- **Repository Link Updates** — Updated all GitHub links to point to the new `VoxVer-Launcher` and `VoxVer-Launcher-docs` repositories
- **Typo Fixes** — Fixed typos like "BMC Launcher AlphaPI" to "BMCLAPI"
- **Missing Feature Documentation** — Added chapters for P2P Instance Sharing, Mod Auto-Update, Theme Customization, Global Keyboard Shortcuts, Skin Management

---

## v0.5.4 - 2026-06-20

> **Theme: Architecture Optimization & Performance Improvement**

### ✨ New Features

- **Squirrel Installer** — Adopt Squirrel auto-update framework, supporting incremental updates and auto rollback
- **Parallel Download Optimization** — Multi-file simultaneous downloads for improved efficiency
- **JVM GC Dynamic Parameters** — Auto-configure optimal garbage collection parameters based on system memory
- **Vitest Testing Framework** — Introduce unit testing to ensure code quality
- **GitHub Actions CI/CD** — Automated build, test and release pipeline

### 🔧 Bug Fixes

- **Archiver ESM Issue** — Fix ESM import issues with archiver library
- **i18n Import Issue** — Fix import path issues in internationalization modules
- **CSP Policy Issue** — Optimize content security policy for correct resource loading

### ⚡ Performance Optimization

- **Startup Speed** — Optimize main process startup flow
- **Memory Usage** — Reduce unnecessary memory allocations

---

## v0.5.3 - 2026-06-09

> **Theme: Stability Update & Experience Optimization**

### ✨ New Features

- **Global Keyboard Shortcuts** — Support custom global shortcuts for quick game launch and window switching
- **Notification System Enhancement** — Optimize notification push logic, support more notification types
- **Theme System Optimization** — Improve dark/light theme switching

### 🔧 Bug Fixes

| Issue | Impact |
|-------|--------|
| **Instance List Refresh** | Fix instance list not updating after refresh |
| **Download Queue Sync** | Fix download queue status synchronization issues |
| **Theme Switch** | Fix styles not applying after theme switch |

### 🎨 UI/UX Optimization

- **Version List Double Cache** — Memory cache + disk cache for faster list loading
- **Skeleton Screen** — Show skeleton screens during data loading for better UX

---

## v0.5.2 - 2026-06-07

> **Theme: P2P Sharing & Theme Customization**

### ✨ New Features

- **P2P Instance Sharing** — WebRTC peer-to-peer technology, 6-digit share code for one-click instance sharing
- **Theme Customization** — Color palette editor with custom theme color schemes
- **CSS Variable Dynamic Calculation** — Auto-calculate related colors based on theme color

### 🔧 Bug Fixes

- **Version List Cache** — Reduce version list request frequency
- **Notification System** — Support more notification types and custom notifications

### ⚡ Performance Optimization

- **List Rendering** — Virtual list technology for better large data rendering performance

---

## v0.5.0 - 2026-06-05

> **Theme: Launch Core Fix & User Experience Optimization**

### ✨ New Features

- **Launcher Auto-Update** — electron-updater based auto-detection and installation
- **Download Management Page** — New sidebar entry for centralized download management
- **Multi-Mirror Download** — Auto-try BMCLAPI, MCBBS and official sources
- **Smart Java Version Matching** — Auto-recommend Java version based on game version
- **Console Chinese Support** — `npm run dev:zh` script for Chinese encoding

### 🔧 Bug Fixes

| Issue | Impact |
|-------|--------|
| **Classpath Passing** | `spawnProcess` missing `classpathStr`, causing empty `-cp` parameter |
| **Version File 404** | Single mirror source missing required files |
| **Version Manifest Timeout** | Missing timeout and retry mechanism |
| **Empty Version Instance** | Show download prompt instead of stale content |
| **JavaInfo Type** | Missing `isDefault` property |
| **Desktop Icon** | Incorrect shortcut icons |

### 🎨 UI/UX Optimization

- **Remove Notification Bell** — Simplify UI by removing PxNotification component
- **Download Management Entry** — Add sidebar option for download management
- **Version Download Prompt** — Prompt user to download version when launching empty instances

---

## v0.4.3 - 2026-06-04

> **Theme: Launch Core Fix & Download Enhancement**

### ✨ New Features

- **Multi-Mirror Download** — Auto-try BMCLAPI, MCBBS and official sources
- **Smart Java Version Matching** — Auto-recommend Java version based on game version
- **ModLoader Inheritance Version Parsing** — Correctly handle Forge/Fabric/NeoForge/Quilt inheritance

### 🔧 Bug Fixes

| Issue | Impact |
|-------|--------|
| **Classpath Passing** | `spawnProcess` missing `classpathStr` |
| **Forge Module System Parameters** | `${library_directory}` / `${classpath_separator}` not replaced |
| **Library Rules** | `checkLibRules` logic error filtering required libraries |
| **Version Manifest** | Missing timeout and retry mechanism |

---

## v0.4.2 - 2026-06-02

> **Theme: Code Standards & Stability Improvement**

### New Features

- **ESLint v9 Configuration** — Unified code style with Prettier formatting
- **Security Configuration Template** — `.env.example` for API Key configuration

### Bug Fixes

- Fixed log level misuse in IPC handler registration
- Fixed ModLoader installation status not displaying correctly
- Fixed global download popup not triggering in certain scenarios

---

## v0.3.0

### New Features

- Mod configuration editor UI (supports toml/json)
- Instance import/export
- ModLoader installation progress connected to frontend
- Global download progress popup
- Notification system frontend integration

### Bug Fixes

- Fixed ModLoader IPC missing issue
- Fixed download progress popup not displaying

---

## v0.2.0

### New Features

- CurseForge + Modrinth dual-source mod downloading
- Mod enable/disable/delete
- Crash monitoring and log analysis
- Skin management

### Bug Fixes

- Fixed Microsoft login token refresh failure
- Fixed launch argument assembly errors for certain versions

---

## v0.1.0

### First Release

- Microsoft account login (Device Code Flow)
- Offline mode
- Game version management (BMCLAPI)
- Fabric / Forge / NeoForge / Quilt installation
- Basic instance system
- Dark theme UI

---

## Planned Features (v0.8.0+)

The following features are being planned and developed, and will be gradually released in subsequent versions:

| Feature | Description | Expected Version |
|---------|-------------|------------------|
| Linux Support | Adapt for Linux platform | v0.8.0+ |

### ✅ Completed Features

| Feature | Completed Version |
|---------|-------------------|
| P2P Instance Sharing | v0.5.2 |
| Theme Customization (Color Palette) | v0.5.2 |
| Modpack Creation Tools | v0.5.2 |
| Global Keyboard Shortcuts | v0.5.3 |
| i18n Internationalization | v0.5.5 |
| Language Switching | v0.5.5 |
| Mod Auto-Update Detection | v0.5.5 |
| UI Architecture Refactor (Settings Categorization) | v0.6.0 |
| Theme System Refactor | v0.6.0 |
| Launch Stability Fixes | v0.6.1 |
| Download Reliability Enhancement | v0.6.1 |
| File Integrity Verification | v0.6.1 |
| Design Token System | v0.6.2 |
| Frosted Glass UI Effect | v0.6.2 |
| Splash Screen Optimization | v0.6.2 |
| HomePage Refactor | v0.6.2 |
| macOS Support | v0.6.4 |
| Design System Completion + Component Library | v0.7.0 |
| Multiplayer Settings | v0.7.0 |
| i18n Full Completion | v0.7.0 |
| Launch Enhancement (Stop Abort + Corrupted File Detection) | v0.7.0 |
| Crash Analysis System | v0.7.1 |
| XMCL Launch Core Integration | v0.7.1 |
| Automatic Java Selection (8/11/17/21/25) | v0.7.1 |
| Lumin UI/UX Design System | v0.7.1 |
| Dual-Channel Update Check (GitHub API Version Comparison) | v0.7.2 |
| Standalone Update Page + Cancel Download | v0.7.3 |
| Multi-Account Card Stack + Loader Adapters + Dark Theme Boost | v0.7.4 |

::: info Note
The planned features above may be adjusted based on development progress and priorities. Actual release dates and feature details are subject to the actual version release.
:::

::: tip Contributing
If you wish to contribute code or suggest features for VoxVer Launcher, feel free to submit a Pull Request or Issue on [GitHub](https://github.com/MeowY-Studios/VoxVer-Launcher).
:::