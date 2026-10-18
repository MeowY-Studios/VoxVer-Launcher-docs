---
title: "Download & Install"
---

# Download & Install

This chapter describes how to download and install VoxVer Launcher, as well as build from source for developers.

## Download

Official releases of VoxVer Launcher are hosted on GitHub Releases.

Go to [GitHub Releases](https://github.com/MeowY-Studios/VoxVer-Launcher/releases) to find the latest version and download the installer.

| File Name | Description | Platform |
|-----------|-------------|----------|
| `VoxVer Launcher Setup x.x.x.exe` | NSIS Installer (Recommended) | Windows |
| `VoxVer Launcher x.x.x.zip` | Portable Version (No Install) | Windows |
| `VoxVer Launcher-x.x.x-arm64.dmg` | macOS ARM64 Installer (Recommended, Apple Silicon) | macOS (Apple Silicon) | Planned |
| `VoxVer Launcher-x.x.x-x64.dmg` | macOS x64 Installer | macOS (Intel) | Planned |

::: tip Recommendation
Regular users should download the **NSIS Installer** for automatic desktop shortcuts and start menu entries, making future updates easier.
:::

## Windows Installation

### Using the Installer

1. Download `VoxVer Launcher Setup x.x.x.exe`
2. Double-click to run the installer
3. If Windows SmartScreen appears, click "More Info" → "Run Anyway"
4. Follow the wizard to select an installation path (default: `C:\Users\<Username>\AppData\Local\Programs\VoxVer Launcher`)
5. Choose whether to create a desktop shortcut
6. Click "Install" and wait for completion
7. VoxVer Launcher will launch automatically after installation

### Using the Portable Version

1. Download `VoxVer Launcher x.x.x.zip`
2. Extract to any directory (avoid paths with Chinese characters or special symbols)
3. Double-click `VoxVer Launcher.exe` to run

::: warning Note
The portable version does not create shortcuts or write to the registry. You need to manually download new versions and replace files for updates.
:::

## macOS Installation

The macOS version is currently **in planning** — no installer is available yet. We are working on the macOS build and will release it soon. Stay tuned on [GitHub Releases](https://github.com/MeowY-Studios/VoxVer-Launcher/releases).

::: tip
The macOS release will be feature-complete with the Windows version and is planned to support ARM64 / x64 dual-architecture.
:::

## Build from Source

If you are a developer or want to try the latest development version, you can build VoxVer Launcher from source.

### Prerequisites

Make sure you have the following installed:

- **Node.js** 24.x or later
- **npm** 9.x or later (included with Node.js)
- **Git** (latest version)

### Clone & Install Dependencies

```bash
# Clone the repository
git clone https://github.com/MeowY-Studios/VoxVer-Launcher.git
cd VoxVer-Launcher

# Install dependencies
npm install
```

### Development Mode

```bash
# Start the development server (hot reload supported)
npm run dev
```

In development mode, the launcher runs with hot-reload support for the frontend.

### Build Installer

```bash
# Build Windows installer
npm run build:win
```

The installer package will be output to the `build/` folder in the project root directory.

## First Launch Checklist

After installation, follow these steps to make sure VoxVer Launcher works properly:

| Step | Action | Description |
|------|--------|-------------|
| 1 | Check Java Path | Go to "Settings" to confirm Java is detected. If not, set it manually. See [Java Settings](/en/guide/java) |
| 2 | Confirm Game Directory | The default game directory is `.minecraft` in the user folder. To change it, see [Custom Path](/en/guide/custom-path) |
| 3 | Add Game Account | Go to "Accounts" to add a Microsoft or offline account. See [Account Management](/en/guide/accounts) |
| 4 | Install Game Version | Go to "Versions", refresh the list, and install the desired version. See [Version Management](/en/guide/versions) |
| 5 | Launch the Game | Return to the home page, select your installed version, and click "Launch" |

If you encounter any issues, please refer to [FAQ](/en/guide/faq) or [Crash Monitor](/en/guide/crash).
