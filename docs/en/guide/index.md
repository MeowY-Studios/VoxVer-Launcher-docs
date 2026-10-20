---
title: "VoxVer Launcher User Guide"
---

# VoxVer Launcher User Guide

Welcome to the **VoxVer Launcher** User Guide. This guide will help you get started from scratch and quickly master all the features of VoxVer Launcher.

## About VoxVer Launcher

VoxVer Launcher is a modern Minecraft launcher built with **Electron + Vue 3 + TypeScript**, designed to provide a clean, efficient, and feature-rich game launching experience. Whether you are a premium player or an offline player, VoxVer Launcher has you covered.

**Core Features:**

- Microsoft authentication (Device Code Flow) + offline mode dual support
- Complete Minecraft version management (Release / Snapshot / Old Alpha / Old Beta / April Fools)
- Fabric / Forge / NeoForge / Quilt ModLoader one-click installation
- Modrinth integration for one-stop mod search, download, and management (CurseForge integration planned)
- Multi-category download view (Vanilla / Mod / Modpack / Datapack / Resource Pack / Shader Pack / Community Resources)
- Instance isolation system with one-click import from HMCL / PCL2 external launchers
- P2P instance sharing via 6-digit code or voxver:// protocol link
- File integrity verification + multi-source download (Official + BMCLAPI)
- Player skin download and rendering
- Design Token system + frosted glass UI effects
- Theme customization with color palette editor for personalized UI
- Global hotkeys for quick game launch
- Auto update (standalone update page, GitHub Releases detection + cancellable download + one-click install)
- Built-in crash monitoring and crash analysis (10 crash signature categories, standalone crash analysis page)
- Data backup and migration
- Custom .minecraft path
- Internationalization (Chinese and English)

## Quick Navigation

| Document | Description | Target Audience |
|----------|-------------|----------------|
| [Download & Install](/en/guide/download) | Download, install, and first launch | All new users |
| [Quick Start](/en/guide/quick-start) | Five steps to first game launch | Users wanting to get started quickly |
| [Account Management](/en/guide/accounts) | Microsoft login, offline mode, multi-account switching | Users managing multiple accounts |
| [Version Management](/en/guide/versions) | Version install, isolation, ModLoader installation | Users managing multiple versions |
| [Mod Management](/en/guide/mods) | Search, download, enable/disable, config editing | Mod users |
| [Instance System](/en/guide/instances) | Create, import, export, independent environment management (temporarily disabled since v0.7.4) | Users needing environment isolation |
| [Java Settings](/en/guide/java) | Auto-detect, manual config, memory tuning | Users with Java issues |
| [Global Settings](/en/guide/settings) | General, appearance, advanced settings | Users wanting personalization |
| [Custom Game Path](/en/guide/custom-path) | Game directory, multi-launcher coexistence | Users needing custom storage |
| [Crash Monitor](/en/guide/crash) | Crash reports, common causes analysis | Users experiencing crashes |
| [FAQ](/en/guide/faq) | Launch, account, mod questions | Users with any issues |
| [Changelog](/en/guide/changelog) | Version changes & roadmap | Users following project progress |

## System Requirements

Before installing VoxVer Launcher, please ensure your system meets the following minimum requirements:

| Item | Minimum Requirement | Recommended |
|------|-------------------|-------------|
| Operating System | Windows 10 64-bit | Windows 10/11 64-bit |
| CPU | x64 architecture | x64 multi-core |
| Memory | 8 GB or more | 16 GB or more |
| Disk Space | 500 MB (launcher only) | SSD, 10 GB+ (with game files) |
| Network | Required for first use | Stable broadband |
| Java | Auto-detected by launcher | Java 17+ (for 1.18+) |

::: tip Note
VoxVer Launcher itself has low hardware requirements, but running Minecraft requires higher specs depending on game version and mod count.
:::

::: tip System Support
Current version supports **Windows**. macOS support is **planned**, and Linux is also in planning. Stay tuned.
:::

## Having Trouble?

If you encounter any issues while using VoxVer Launcher:

1. **Check the documentation** -- Browse the [FAQ](/en/guide/faq) and [Crash Monitor](/en/guide/crash) sections first; most issues can be resolved there.
2. **Search Issues** -- Check [GitHub Issues](https://github.com/MeowY-Studios/VoxVer-Launcher/issues) for similar problems.
3. **Submit Issue** -- If nothing helps, create a new GitHub Issue with crash logs and system info for faster debugging.
