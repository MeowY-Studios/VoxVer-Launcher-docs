---
title: "Quick Start"
---

# Quick Start

This guide walks you through launching the game for the first time in five steps. If you are using VoxVer Launcher for the first time, please follow the procedure below.

## Step Overview

```
Install VoxVer Launcher
    |
    v
Step 1: Add Account (Microsoft Login / Offline Mode)
    |
    v
Step 2: Install Game Version (Refresh List -> Select Version -> Install)
    |
    v
Step 3: Install ModLoader (Optional, only needed for mods)
    |
    v
Step 4: Configure Java (Optional, auto-detection usually works)
    |
    v
Step 5: Launch Game
```

## Step 1: Add Account

Open VoxVer Launcher and go to the **Accounts** page in the left sidebar. VoxVer Launcher supports two login methods:

### Microsoft Login

If you own a Minecraft Java Edition account, Microsoft login is recommended:

1. Click **"Microsoft Login"** on the Accounts page
2. The launcher will open your default browser and display a device code (e.g., `A1B2C3D4`)
3. Sign in to your Microsoft account in the browser (if not already signed in)
4. Go to [microsoft.com/devicelogin](https://microsoft.com/devicelogin) and enter the device code shown on the page
5. Complete the authorization as prompted
6. Return to VoxVer Launcher; the launcher will automatically retrieve and save the access token
7. After a successful login, your avatar and username will appear in the account list

::: tip
After the first login, VoxVer Launcher will automatically refresh the token, so no re-login is needed afterwards. See [Account Management](/en/guide/accounts) for details.
:::

### Offline Mode

If you only need to play single-player or test the game, you can use offline mode:

1. Click **"Offline Login"** on the Accounts page
2. Enter the desired username (any alphanumeric characters) in the dialog
3. Click "Confirm" to complete the login

::: warning
Offline mode cannot connect to official servers (such as Hypixel). It is only suitable for single-player or LAN play.
:::

## Step 2: Install Game Version

Go to the **Versions** page in the left sidebar:

1. Click **"Refresh Version List"** — VoxVer Launcher will fetch the latest version list from the BMCLAPI mirror
2. Select the desired game version:
   - **Releases** — Stable versions, recommended for most players
   - **Snapshots** — Development versions, may contain bugs
   - **Old Versions** — Early historical versions
   - **April Fools** — Special versions released every April Fools' Day
3. After selecting a version, click **"Install"**
4. Wait for the download to complete; installation progress is shown in the global download popup at the bottom-right

::: info First Download
When installing a game version for the first time, VoxVer Launcher needs to download core game files, resource files, and library files. The total size is typically between 200MB and 500MB, depending on the version. Please ensure a stable internet connection and wait patiently for the download to complete.
:::

## Step 3: Install ModLoader (Optional)

If you plan to use mods, you need to install the corresponding ModLoader first:

1. On the **Versions** page, find the installed vanilla game
2. Click the **"Install ModLoader"** button next to that version
3. Choose your desired ModLoader:

| ModLoader | Features | Recommended For |
|-----------|----------|-----------------|
| Fabric | Lightweight, fast loading, broad mod compatibility | Players prioritizing performance and compatibility |
| Forge | Established loader, mature ecosystem, great for large mods | Players using large modpacks |
| NeoForge | Forge's successor, designed for newer versions | Recommended for 1.20+ |
| Quilt | Fabric fork, more modular | Players needing advanced modular features |

4. Select the version, confirm, and wait for the installation to complete.

## Step 4: Configure Java (Optional)

VoxVer Launcher will automatically detect installed Java environments on first launch. If detection succeeds, you can skip this step.

If auto-detection fails, or if you need to use a specific Java version, see [Java Settings](/en/guide/java) for manual configuration.

## Step 5: Launch Game

From the VoxVer Launcher home page, click the launch area next to the **"Downloads"** button in the quick actions, or navigate directly to the **Launch** page:

1. Make sure the correct account is selected (in the account dropdown)
2. Make sure the correct game version is selected
3. Click **"Launch Game"**
4. Wait for the progress bar to complete; the game window will open automatically

::: tip
During the launch process, VoxVer Launcher will automatically verify game file integrity, download any missing dependencies, and assemble the correct launch parameters. This usually takes 5–30 seconds — actual startup time depends on your computer's configuration.
:::

## Having Trouble?

- **Launch failed or crash?** Check [Crash Monitor](/en/guide/crash) to learn how to view error logs and troubleshoot.
- **Java error?** Go to **Settings** and manually specify the Java path. See [Java Settings](/en/guide/java).
- **Other issues?** See the [FAQ](/en/guide/faq).
