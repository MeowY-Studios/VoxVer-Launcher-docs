---
title: "Crash Monitor"
---

# Crash Monitor

VoxVer Launcher has a built-in crash monitoring system that automatically captures runtime logs when the game exits unexpectedly, analyzes the error cause, and provides repair suggestions. This chapter covers how to view crash reports, understand report contents, and handle common crash issues.

## View Crash Reports

When a game crash occurs, VoxVer Launcher automatically records the crash information. You can view historical crash records at any time.

### Steps

1. Go to the **Home** page or **Settings** page
2. Find and click the **"Crash Records"** entry, or go directly to the standalone **Crash Analysis page** (`/crash-analysis`)
3. The crash record list shows all historical crash entries, sorted in reverse chronological order
4. Click on a record to view the detailed crash analysis report

::: tip Crash Analysis Page
Since v0.7.1, VoxVer Launcher provides a standalone "Crash Analysis" page (`/crash-analysis`) with a report history list, severity labels, exception types and stack details. The launch page crash panel also shows error descriptions, possible causes and suggested solutions. Crash report parsing supports **10 crash signature categories**.
:::

### Crash Report Contents

Each crash analysis report contains the following information:

| Field | Description | Example |
|-------|-------------|---------|
| Timestamp | The exact time the crash occurred | 2025-01-15 14:32:08 |
| Game Version | Minecraft version at the time of the crash | 1.20.4 |
| ModLoader | ModLoader and version in use | Fabric Loader 0.15.6 |
| Severity | Crash severity label | Critical / Warning |
| Error Type | Classification of the root cause | `java.lang.OutOfMemoryError` |
| Stack Details | Exception type and call stack | `Exception in thread "Render thread"` |
| Log Snippet | Key log excerpt surrounding the crash | `Exception in thread "Render thread"` |
| Analysis Suggestions | Auto-generated repair suggestions | "Consider increasing the maximum memory to 4096MB" |

## Common Crash Causes and Solutions

Below are common game crash causes and their corresponding solutions:

| Crash Cause | Error Signature | Solution |
|-------------|-----------------|----------|
| Java out of memory | `OutOfMemoryError`, `Java heap space` | Increase the maximum memory setting (recommended 4096MB or higher), see [Java Settings](/guide/java) |
| Mod conflict | `ConcurrentModificationException`, `NoSuchMethodError` | Disable recently added mods one by one to identify the conflicting mod and remove it |
| Java version mismatch | `UnsupportedClassVersionError`, `Unsupported major minor version` | Ensure the Java version meets game requirements (1.17+ requires Java 16+, 1.18+ requires Java 17+) |
| ModLoader version mismatch | Loader version error on startup | Reinstall the ModLoader version that matches the game version |
| Missing dependency mod | `ClassNotFoundException`, `NoClassDefFoundError` | Check the class name mentioned in the error and install the corresponding dependency mod |
| Native library load failure | `UnsatisfiedLinkError`, `java.lang.UnsatisfiedLinkError` | Reinstall the game version to repair native library files |
| Shader crash | Render-related errors, `GL error` | Disable or change the shader pack, ensure the graphics driver is up to date |
| Corrupted file | `IOException`, `CorruptedJarException` | Delete the corresponding file and re-download it, or reinstall from the version page |

## Crash Troubleshooting Flow

When encountering a game crash, it is recommended to follow this troubleshooting flow:

```
Game crashes
  |
  v
Check the "Error Type" in the crash report
  |
  v
Refer to the table above to find possible causes based on error type
  |
  v
Try the corresponding solution
  |
  v
Issue resolved? --Yes--> Play normally
  |
  No
  v
Try disabling all mods and launching again
  |
  v
Launches normally? --Yes--> Enable mods one by one to find the conflicting one
  |                        |
  No                       v
  v                     Remove the conflicting mod or find a replacement
Reinstall the game version
  |
  v
Issue persists? --> Submit a bug report
```

## Submit a Bug Report

If you have tried all the above methods and still cannot resolve the issue, you can submit a bug report to the VoxVer Launcher development team for further assistance.

### Steps

1. Locate the crash report in VoxVer Launcher's crash records
2. Click the **"Export Report"** button to export the crash information as a file
3. Go to [GitHub Issues](https://github.com/MeowY-Studios/VoxVer-Launcher/issues)
4. Click "New Issue" to create a new issue report
5. Include the following information in the report:
   - **Operating system version** (e.g., Windows 11 23H2)
   - **VoxVer Launcher version** (e.g., v0.3.0)
   - **Java version** (e.g., Java 17.0.9)
   - **Game version** (e.g., 1.20.4)
   - **ModLoader and version** (e.g., Fabric Loader 0.15.6)
   - **List of installed mods** (if using mods)
   - **Crash report content** (the exported crash information file)
   - **Steps to reproduce** (if the crash is reproducible)

::: tip
A detailed and complete bug report helps developers locate and fix issues more quickly. Please try to provide all relevant information.
:::
