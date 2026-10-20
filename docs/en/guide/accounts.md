---
title: "Account Management"
---

# Account Management

VoxVer Launcher supports multiple login methods to suit different gameplay needs. This chapter covers Microsoft account login, offline mode, multi-account management, and skin management.

## Microsoft Login

Microsoft login uses the **Device Code Flow** authentication method, which is both secure and convenient. No password is required to be entered in the launcher.

### Login Steps

1. Go to the **Accounts** page
2. Click **"Microsoft Login"**
3. The launcher displays a device code and an authorization URL
4. Open the authorization URL in your browser
5. Enter the device code on the browser page
6. Follow the prompts to complete the authorization
7. The launcher automatically retrieves and saves the account token

### Token Management

- Tokens are **encrypted and stored** using Electron safeStorage
- Tokens are **automatically refreshed**, eliminating the need for repeated logins
- If a token expires, the launcher will automatically attempt to refresh it

## Offline Mode

Offline mode allows you to play without a Microsoft account, suitable for single-player or testing.

### Setting Up

1. Go to the **Accounts** page
2. Click **"Offline Login"**
3. Enter any username of your choice
4. Click "Confirm"

::: warning Note
Offline mode can only play on the current device and cannot connect to online servers that require authentication.
:::

## Skin Management

VoxVer Launcher supports viewing and managing Minecraft player skins. Skins are automatically cached locally for quick loading.

### Skin Cache Mechanism

When a player's skin is retrieved, the launcher caches it locally. The cache location is:

```
<VoxVer Launcher Data Directory>/skins/
```

The cache files are organized by UUID for automatic lookup and cleanup.

### Viewing a Skin

Once logged in, you can view the skin on the account details page. The launcher downloads and displays the **face render** and **full-body render** of the skin.

### Managing Skin Cache

| Operation | Description |
|-----------|-------------|
| Refresh Skin | Force re-download the latest skin from the server |
| Clear Cache | Delete all locally cached skin files |

::: tip Tip
The skin cache helps reduce server requests and speeds up skin loading. Clearing the cache can force the launcher to re-download the latest skin, but it will require a one-time network download.
:::

## Multi-Account Management

Since v0.7.4, the accounts page is rebuilt as a **card-stack style multi-account manager**: multiple Microsoft accounts coexist as cards, each with a 3D skin preview (SkinViewer3D); click a card to quickly switch the active account. New accounts are added through the standalone `MicrosoftLoginModal` login dialog.

### Switching Accounts

1. Go to the **Accounts** page
2. Find the target account card in the stack
3. Click the card to set it as the active account
4. The Launch page will show the current account accordingly

## Remove Account

If you no longer need a particular account, you can remove it.

### Removal Steps

1. Go to the **Accounts** page
2. Find the account you want to remove
3. Click **"Remove"**
4. Confirm in the dialog

::: warning Note
Removing an account does **not** delete game data, mods, or saves. It only clears the saved token and profile information. You will need to log in again if you wish to use this account in the future.
:::
