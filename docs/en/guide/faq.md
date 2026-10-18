---
title: "FAQ"
---

# FAQ

This chapter compiles the most frequently encountered issues and their solutions when using VoxVer Launcher. If your issue is not listed here, please refer to [Crash Monitor](/guide/crash) or submit feedback via [GitHub Issues](https://github.com/MeowY-Studios/VoxVer-Launcher/issues).

## Launch Issues

### "Java not found" error on launch?

**Cause**: VoxVer Launcher cannot detect a valid Java runtime environment on your system.

**Solution**:

1. Go to the **Settings** page and locate the "Java Settings" section
2. Click the **"Auto-Detect"** button to rescan for Java on your system
3. If still not detected, manually specify the Java path:
   - Click **"Browse"**, navigate to the `bin` folder of your Java installation directory
   - Select the `java.exe` file
   - Save the settings
4. If Java is not installed on your system, download and install it from [Eclipse Temurin](https://adoptium.net/)

See [Java Settings](/guide/java) for details.

### Game crashes immediately after launch?

**Cause**: There could be multiple reasons for crashing, including insufficient memory, mod conflicts, Java version mismatch, etc.

**Troubleshooting Steps**:

1. Check the crash report in **Crash Monitor** to identify the specific error type
2. Try the following solutions based on the error type:

| Error Type | Solution |
|------------|----------|
| `OutOfMemoryError` | Increase the maximum memory setting to 4096MB or higher |
| Mod-related errors | Disable all mods and try launching, then enable them one by one to find the conflicting mod |
| `UnsupportedClassVersionError` | Install a Java version that matches the game version |
| Native library errors | Reinstall the game version |

See [Crash Monitor](/guide/crash) for details.

### Launch button grayed out and cannot click?

**Possible Causes**:

- No game account selected -- Please add an account on the **Accounts** page first
- No game version installed -- Please install at least one version on the **Versions** page first
- Download or installation in progress -- Please wait for the current operation to complete

## Account Issues

### Microsoft login stuck?

**Possible Causes and Solutions**:

| Cause | Solution |
|-------|----------|
| Device code entered incorrectly | Double-check the device code displayed by the launcher and ensure it is entered correctly |
| Browser logged into the wrong Microsoft account | Sign out of the current Microsoft account in the browser and sign in with the correct one |
| Token retrieval delay | Wait patiently for 1-2 minutes; network latency may slow down token retrieval |
| Browser blocked | Check if the firewall or security software is blocking the browser from accessing Microsoft servers |
| Microsoft service temporarily unavailable | Try again later, or check the [Xbox Live Status page](https://status.xboxlive.com/) |

### Can I play on premium servers with offline mode?

**No.** Offline mode is only suitable for the following scenarios:

- Single-player games (Survival / Creative / Adventure)
- LAN multiplayer (when open to LAN is enabled)
- Servers that support offline authentication (very rare)

To connect to premium servers (such as Hypixel, 2b2t, etc.), you must use Microsoft authentication.

### "Invalid token" after Microsoft login?

**Cause**: The saved access token has expired or been revoked.

**Solution**:

1. Go to the **Accounts** page
2. Remove the currently invalid Microsoft account
3. Re-initiate Microsoft login (Device Code Flow)
4. If the issue persists, check whether your Microsoft account password has been changed

## Mod Issues

### Installed mods not working?

Check the following list item by item:

1. **Confirm ModLoader is installed** -- Go to the "Versions" page and check if the corresponding ModLoader (Fabric / Forge / NeoForge / Quilt) is installed for the target version
2. **Confirm mod type matches** -- Fabric mods can only be loaded in a Fabric environment; Forge mods can only be loaded in a Forge environment
3. **Confirm game version compatibility** -- Check whether the supported version listed in the mod description matches your installed game version
4. **Confirm the mod is enabled** -- Check whether the mod's toggle switch is turned on in the instance details
5. **Check for dependency mods** -- Some mods require dependency mods (such as Cloth Config, GeckoLib, etc.), so check the mod's description page
6. **Confirm file integrity** -- An interrupted download may result in an incomplete mod file; try re-downloading

### Modrinth download failed?

**Possible Causes and Solutions**:

| Cause | Solution |
|-------|----------|
| Network connection issues | Check whether your network connection is normal |
| Download source unavailable | Go to **Settings** to switch the download source |
| Blocked by firewall | Check your firewall or security software settings |
| Insufficient disk space | Free up disk space and try again |
| Repository service maintenance | Try again later; Modrinth occasionally undergoes maintenance |

::: info About CurseForge
CurseForge integration is currently **planned** (API key pending approval) and is not available in this version.
:::

## Other

### Where are game saves located?

The save location depends on your configuration:

| Scenario | Save Path |
|----------|-----------|
| Default configuration | `.minecraft/saves/` |
| Version isolation enabled | `.minecraft/versions/<version-name>/saves/` |
| Using the instance system | `saves/` folder within the instance directory |
| Custom game directory | `<custom-path>/saves/` |

::: tip
It is recommended to regularly back up your save folder to prevent accidental data loss.
:::

### How to completely uninstall VoxVer Launcher?

If you decide to uninstall VoxVer Launcher, follow these steps:

1. **Uninstall the launcher program**
   - Uninstall VoxVer Launcher via "Programs and Features" in the Windows Control Panel
   - Or run the installer and select the "Uninstall" option

2. **Delete game data** (optional)
   - Delete the game directory (default `.minecraft` folder)
   - Note: This will delete all game versions, mods, saves, and configurations

3. **Delete launcher configuration** (optional)
   - Delete VoxVer Launcher's application data directory (usually located in `AppData/Roaming/VoxVer Launcher/` or `AppData/Local/VoxVer Launcher/`)

::: warning Important
Before uninstalling, it is recommended to **export important instances** as a backup. See the export feature in [Instance System](/guide/instances).
:::

### Does VoxVer Launcher support macOS or Linux?

VoxVer Launcher currently supports **Windows**. macOS support is **planned** (ARM64 / x64 dual architecture), and Linux is also in planning. Stay tuned.

### How to update VoxVer Launcher?

- **Installer version**: VoxVer Launcher automatically detects new versions and prompts you to update. You can also manually download the latest version from [GitHub Releases](https://github.com/MeowY-Studios/VoxVer-Launcher/releases) and install it over the existing installation.
- **Portable version**: You need to manually download the new version and replace the files. It is recommended to keep the configuration files and only replace the program files.
