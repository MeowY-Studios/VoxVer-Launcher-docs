---
title: "VoxVer Launcher 使用指南"
---

# VoxVer Launcher 使用指南

欢迎使用 **VoxVer Launcher** 使用指南。本指南将帮助你从零开始，快速掌握 VoxVer Launcher 启动器的全部功能。

## 关于 VoxVer Launcher

VoxVer Launcher 是一款基于 **Electron + Vue 3 + TypeScript** 技术栈打造的现代化 Minecraft 启动器，致力于为玩家提供简洁、高效、功能丰富的游戏启动体验。无论你是正版玩家还是离线玩家，VoxVer Launcher 都能满足你的需求。

**核心特性：**

- 微软正版登录（Device Code Flow）与离线模式双支持
- 完整的 Minecraft 版本管理（正式版 / 快照 / 远古版 / 愚人节版）
- Fabric / Forge / NeoForge / Quilt 四大 ModLoader 一键安装
- 接入 Modrinth，Mod 搜索、下载、管理一站式操作（CurseForge 接入计划中）
- 多分类下载视图（原版游戏 / Mod / 整合包 / 数据包 / 资源包 / 光影包 / 社区资源）
- 实例隔离系统，支持从 HMCL / PCL2 外部启动器一键导入
- P2P 实例分享，通过 6 位分享码或 voxver:// 协议链接一键分享
- 文件完整性校验 + 多源下载（官方源 + BMCLAPI）
- 玩家皮肤下载与渲染
- Design Token 设计体系 + 磨砂玻璃 UI 效果
- 主题自定义，色盘编辑器打造个性化界面
- 全局快捷键，快速启动游戏
- 自动更新（独立版本更新页，GitHub Releases 检测 + 可取消下载 + 一键安装）
- 内置崩溃监控与崩溃分析（10 类崩溃特征识别，独立崩溃分析页面）
- 数据备份与迁移
- 自定义 .minecraft 路径
- 国际化支持，简体中文和英文

## 快速导航

| 章节 | 说明 | 适合人群 |
|------|------|---------|
| [下载与安装](/guide/download) | 获取安装包、安装步骤、从源码构建 | 所有新用户 |
| [快速启动](/guide/quick-start) | 五步完成首次游戏启动 | 希望快速上手的用户 |
| [账户管理](/guide/accounts) | 微软登录、离线模式、多账户切换 | 需要管理多个账户的用户 |
| [版本管理](/guide/versions) | 版本安装、隔离、ModLoader 安装 | 需要管理多个版本的用户 |
| [Mod 管理](/guide/mods) | 搜索、下载、启用/禁用、配置编辑 | 使用 Mod 的玩家 |
| [实例系统](/guide/instances) | 创建、导入、导出、独立环境管理（v0.7.4 起暂时停用） | 需要多环境隔离的玩家 |
| [Java 设置](/guide/java) | 自动检测、手动配置、内存调优 | 遇到 Java 相关问题的用户 |
| [全局设置](/guide/settings) | 常规、外观、高级设置详解 | 希望个性化配置的用户 |
| [自定义游戏路径](/guide/custom-path) | 游戏目录设置、多启动器共存 | 需要自定义存储位置的用户 |
| [崩溃监控](/guide/crash) | 崩溃报告查看、常见原因分析 | 遇到游戏崩溃的用户 |
| [常见问题](/guide/faq) | 启动、账户、Mod 等问题解答 | 遇到任何问题的用户 |
| [更新日志](/guide/changelog) | 各版本功能变更与计划路线图 | 关注项目进展的用户 |

## 系统要求

在安装 VoxVer Launcher 之前，请确认你的系统满足以下最低要求：

| 项目 | 最低要求 | 推荐配置 |
|------|---------|---------|
| 操作系统 | Windows 10 64 位 | Windows 10/11 64 位 |
| 处理器 | x64 架构处理器 | x64 架构多核处理器 |
| 内存 | 8 GB 及以上 | 16 GB 及以上 |
| 磁盘空间 | 500 MB（启动器本身） | SSD，10 GB+（含游戏文件） |
| 网络 | 首次使用需联网下载资源 | 稳定的宽带连接 |
| Java | 启动器可自动检测系统 Java | Java 17+（适配 1.18+ 版本） |

::: tip 提示
VoxVer Launcher 启动器本身对硬件要求较低，但运行 Minecraft 游戏需要更高的硬件配置，具体取决于你游玩的游戏版本和安装的 Mod 数量。
:::

::: tip 系统支持
当前版本已支持 **Windows** 平台。macOS 版本仍在 **计划中**，Linux 版本也在开发计划中，敬请期待。
:::

## 遇到问题？

如果你在使用 VoxVer Launcher 的过程中遇到任何问题，可以通过以下方式获取帮助：

1. **查阅文档** -- 先浏览本指南中的 [常见问题](/guide/faq) 和 [崩溃监控](/guide/crash) 章节，大部分问题都能在这里找到答案。
2. **搜索 Issues** -- 前往 [GitHub Issues](https://github.com/MeowY-Studios/VoxVer-Launcher/issues) 搜索是否已有相同问题的讨论。
3. **提交 Issue** -- 如果以上方式都无法解决你的问题，请在 GitHub 提交新的 Issue，并尽量附上崩溃日志和系统环境信息，以便开发者快速定位问题。
