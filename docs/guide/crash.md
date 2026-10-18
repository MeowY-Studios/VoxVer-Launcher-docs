---
title: "崩溃监控"
---

# 崩溃监控

VoxVer Launcher 内置了崩溃监控系统，能够在游戏异常退出时自动捕获运行日志、分析错误原因，并给出修复建议。本章将介绍如何查看崩溃报告、理解报告内容以及处理常见的崩溃问题。

## 查看崩溃报告

当游戏发生崩溃时，VoxVer Launcher 会自动记录崩溃信息。你可以随时查看历史崩溃记录。

### 查看步骤

1. 进入 **首页** 或 **设置** 页面
2. 找到并点击 **「崩溃记录」** 入口，或直接进入独立的 **「崩溃分析」页面**（`/crash-analysis`）
3. 在崩溃记录列表中可以看到所有历史崩溃条目，按时间倒序排列
4. 点击某条记录，即可查看详细的崩溃分析报告

::: tip 崩溃分析页面
自 v0.7.1 起，VoxVer Launcher 提供独立的「崩溃分析」页面（`/crash-analysis`），包含历史报告列表、严重程度标签、异常类型与堆栈详情；启动页的崩溃面板也会展示错误描述、可能原因与建议解决方案。崩溃报告解析支持 **10 类崩溃特征识别**。
:::

### 崩溃报告内容

每条崩溃分析报告包含以下信息：

| 字段 | 说明 | 示例 |
|------|------|------|
| 时间戳 | 崩溃发生的精确时间 | 2025-01-15 14:32:08 |
| 游戏版本 | 崩溃时的 Minecraft 版本 | 1.20.4 |
| ModLoader | 使用的 ModLoader 及版本 | Fabric Loader 0.15.6 |
| 严重程度 | 崩溃严重程度标签 | 严重 / 警告 |
| 错误类型 | 崩溃的根本原因分类 | `java.lang.OutOfMemoryError` |
| 堆栈详情 | 异常类型与调用堆栈 | `Exception in thread "Render thread"` |
| 日志片段 | 崩溃前后的关键日志 | `Exception in thread "Render thread"` |
| 分析建议 | VoxVer Launcher 自动生成的修复建议 | 「建议增大最大内存至 4096MB」 |

## 常见崩溃原因及解决方案

以下是游戏崩溃的常见原因和对应的解决方法：

| 崩溃原因 | 错误特征 | 解决方案 |
|---------|---------|---------|
| Java 内存不足 | `OutOfMemoryError`、`Java heap space` | 增大最大内存设置（建议 4096MB 以上），详见 [Java 设置](/guide/java) |
| Mod 冲突 | `ConcurrentModificationException`、`NoSuchMethodError` | 逐个禁用最近添加的 Mod，找出冲突的 Mod 并移除 |
| Java 版本不匹配 | `UnsupportedClassVersionError`、`Unsupported major minor version` | 确认 Java 版本符合游戏要求（1.17+ 需 Java 16+，1.18+ 需 Java 17+） |
| ModLoader 版本不匹配 | 启动时提示 Loader 版本错误 | 重新安装与游戏版本匹配的 ModLoader |
| 缺少前置 Mod | `ClassNotFoundException`、`NoClassDefFoundError` | 检查报错中提到的类名，安装对应的前置 Mod |
| 原生库加载失败 | `UnsatisfiedLinkError`、`java.lang.UnsatisfiedLinkError` | 重新安装游戏版本以修复原生库文件 |
| 着色器/光影崩溃 | 渲染相关错误、`GL error` | 禁用或更换光影包，确认显卡驱动为最新版本 |
| 文件损坏 | `IOException`、`CorruptedJarException` | 删除对应文件并重新下载，或在版本页面重新安装 |

## 崩溃排查流程

遇到游戏崩溃时，建议按以下流程进行排查：

```
游戏崩溃
  |
  v
查看崩溃报告中的「错误类型」
  |
  v
根据错误类型对照上表找到可能的原因
  |
  v
尝试对应的解决方案
  |
  v
问题解决？ --是--> 正常游戏
  |
  否
  v
尝试禁用所有 Mod 后启动
  |
  v
能正常启动？ --是--> 逐个启用 Mod 找出冲突项
  |                    |
  否                   v
  v                 移除冲突 Mod 或寻找替代品
重新安装游戏版本
  |
  v
问题仍存在？ --> 提交错误报告
```

## 提交错误报告

如果你尝试了以上所有方法仍无法解决问题，可以向 VoxVer Launcher 开发团队提交错误报告，以获得进一步的帮助。

### 提交步骤

1. 在 VoxVer Launcher 的崩溃记录中找到对应的崩溃报告
2. 点击 **「导出报告」** 按钮，将崩溃信息导出为文件
3. 前往 [GitHub Issues](https://github.com/MeowY-Studios/VoxVer-Launcher/issues)
4. 点击「New Issue」创建新的问题报告
5. 在报告中包含以下信息：
   - **操作系统版本**（如 Windows 11 23H2）
   - **VoxVer Launcher 版本**（如 v0.3.0）
   - **Java 版本**（如 Java 17.0.9）
   - **游戏版本**（如 1.20.4）
   - **ModLoader 及版本**（如 Fabric Loader 0.15.6）
   - **已安装的 Mod 列表**（如果使用了 Mod）
   - **崩溃报告内容**（导出的崩溃信息文件）
   - **复现步骤**（如果能稳定复现）

::: tip 提示
详细且完整的错误报告能够帮助开发者更快地定位和修复问题。请尽量提供所有相关信息。
:::
