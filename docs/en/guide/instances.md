---
title: "Instance System"
---

# Instance System

::: warning Temporarily Disabled Since v0.7.4
Starting from v0.7.4, the instance module is temporarily disabled and the instances page shows a "Not Available Yet" placeholder. Existing instance data is unaffected and the module will return in a future release. This page is kept for reference and describes the module's behavior once restored.
:::

The instance system is one of the core features of VoxVer Launcher. It allows you to create completely independent Minecraft environments for different playstyles. Each instance has its own game version, mods, configurations, and saves, all isolated from one another. This chapter covers instance creation, import, export, and the isolation mechanism in detail.

## Create Instance

By creating instances, you can set up independent environments for different gaming scenarios — for example, one for vanilla survival, one for modded adventure, and one for creative mode testing.

### Steps

1. Go to the **Instances** page
2. Click the **"New Instance"** button
3. Fill in the following information in the creation wizard:
   - **Instance Name** — Give the instance a recognizable name (e.g., "Survival Modpack", "Test Environment")
   - **Game Version** — Select the base game version from the dropdown list
   - **ModLoader** — Choose the ModLoader to install (optional; you can also install it after creation)
   - **ModLoader Version** — Select the specific ModLoader version
4. Click the **"Create"** button
5. VoxVer Launcher will automatically create the instance directory structure and install the selected version and ModLoader

::: tip
After creation, you can further manage the instance's mods, configurations, and other settings on the **Instance Details** page.
:::

## Import Instance

If you have used Minecraft with another launcher before, or have an existing `.minecraft` directory, you can import it as a VoxVer Launcher instance.

### Steps

1. Go to the **Instances** page
2. Click the **"Import"** button
3. Browse in the file picker and select an existing `.minecraft` directory (or one of its subdirectories)
4. VoxVer Launcher will automatically scan the directory for game versions, mods, and configuration files
5. Review the import information and click **"Confirm"**
6. Wait for the import to complete

::: info
During the import process, VoxVer Launcher will identify the game version and ModLoader already present in the directory and automatically create the corresponding instance configuration. Existing game files will not be moved or modified.
:::

### Import from External Launchers

Starting from v0.6.3, VoxVer Launcher supports automatically detecting and importing game instance data from **HMCL (Hello Minecraft! Launcher)** and **PCL2 (Plain Craft Launcher 2)**.

1. Go to the **Instances** page
2. Click the **"Import"** button and select "Import from External Launcher"
3. VoxVer Launcher will automatically scan the system for installed HMCL and PCL2 data directories
4. Detected instances will display instance name, game version, ModLoader type, and mod count
5. Select the instances to import and click "Confirm Import"
6. After import, the instances will appear in VoxVer Launcher's instance list

::: tip Advantages
- **Seamless Migration** — Migrate HMCL or PCL2 instance data to VoxVer Launcher in one click
- **Preserve Original Data** — Original launcher data will not be modified or deleted
- **Smart Detection** — Automatically parse instance game version, ModLoader, and mod information
:::

## Export Instance

You can package an instance for export, making it easy to share with other players or back up your saves.

### Steps

1. Go to the **Instance Details** page
2. Click the **"Export"** button
3. Choose the export path and file name
4. Select the content to include (optional):
   - Whether to include save files
   - Whether to include mod files
   - Whether to include configuration files
5. Click **"Confirm"** and wait for the packaging to complete

::: tip
The exported instance archive can be shared with other VoxVer Launcher users, who can use it via the **Import** feature. It can also serve as a backup method for your saves.
:::

## Instance Isolation

The core advantage of the instance system is **complete isolation**. Each instance is an independent Minecraft environment with its own file directory.

### Isolated Items

| Item | Directory | Description |
|------|-----------|-------------|
| Game Version | `versions/` | Each instance uses its own game version JAR and JSON files |
| Mod Files | `mods/` | Mods in each instance do not affect each other; different instances can install different versions of the same mod |
| Configuration | `config/` | Mod configurations are stored independently per instance; modifying one instance's config does not affect others |
| Save Data | `saves/` | Saves are completely independent across instances, preventing save conflicts |
| Resource Packs | `resourcepacks/` | Each instance can use a different combination of resource packs |
| Log Files | `logs/` | Runtime logs are recorded independently for each instance, making it easier to troubleshoot issues |

### Example Directory Structure

```
instances/
  └── My Survival World/
      ├── versions/          # Game version files
      ├── mods/              # Mod files
      ├── config/            # Mod configurations
      ├── saves/             # Game saves
      ├── resourcepacks/     # Resource packs
      └── logs/              # Runtime logs
```

::: tip Usage Suggestions
- **Multi-version players**: Create a separate instance for each commonly used game version to avoid reinstalling mods when switching versions.
- **Mod players**: Create separate instances for different types of modpacks, such as "Performance Optimization", "Adventure", and "Tech" packs.
- **Testers**: Create a dedicated test instance to try out new mods or configurations without affecting your main saves.
:::

## P2P Instance Sharing

VoxVer Launcher features built-in **P2P instance sharing**, based on **WebRTC direct connection technology**, allowing you to share your game instances with friends without uploading to any server.

### How It Works

```
Sender                            VoxVer Signaling Server                  Receiver
  |                                       |                                   |
  |-- Generate share code (6 digits) ---->|                                   |
  |<-- Share code ------------------------|                                   |
  |                                       |<-- Enter share code -------------|
  |                                       |-- Forward match request -------->|
  |<-- Establish WebRTC direct channel ---|                                   |
  |-- Encrypted instance data transfer -------------------------------->     |
  |<-- Transfer complete ----------------------------------------------------|
```

### Share an Instance

1. Go to the **Instance Details** page
2. Click the **"Share"** button
3. The launcher will automatically generate a **6-digit share code** (e.g., `A1B2C3`)
4. Share the code with your friend
5. Wait for your friend to accept the connection, then the transfer will begin

### Receive an Instance

1. Go to the **Instances** page
2. Click the **"Receive Share"** button
3. Enter the 6-digit share code provided by your friend
4. Wait for the connection to be established
5. Review the import information and complete the transfer

::: tip Quick Receive - voxver:// Protocol
Your friend can share directly via a link: `voxver://share:<code>` (e.g., `voxver://share:A1B2C3`). Clicking the link will automatically open VoxVer Launcher and navigate to the receive page — no need to manually enter the share code. This works via VoxVer Launcher's registered custom URL protocol.
:::

### Sharing Options

| Option | Description |
|--------|-------------|
| Include Saves | Whether to include game saves from the `saves/` directory |
| Include Mods | Whether to include mod files from the `mods/` directory |
| Include Configs | Whether to include mod configurations from the `config/` directory |
| Include Resource Packs | Whether to include files from the `resourcepacks/` directory |

### Features & Safety

::: tip Key Advantages
- **Direct transfer** — Based on WebRTC P2P direct connection, offering fast transfer speeds with no rate limiting
- **No server relay** — The launcher only handles signaling negotiation; instance data never passes through any third-party servers
- **Privacy & security** — Your instance data is transmitted directly between you and the recipient
- **Easy to use** — Just a 6-digit share code to establish a connection
:::

::: warning Notes
- The share code is valid for **5 minutes by default**; you will need to regenerate it if it expires.
- Both parties need to be online at the same time to complete the share.
- The recipient needs to have the same (or compatible) game version installed as the sender.
:::
