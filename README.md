# VoxVer Launcher

**VoxVer Launcher** — 一个现代化的 Minecraft 启动器

[中文文档](https://nnkmn.github.io/VoxVer-Launcher-docs/) | [English Docs](https://nnkmn.github.io/VoxVer-Launcher-docs/en/)

## ✨ 特性

- 🔐 **微软正版登录** — Device Code Flow 认证，token 自动刷新，多账户切换
- 🚀 **游戏启动** — XMCL 启动核心，Java 版本自动匹配，启动进度实时推送
- 📦 **版本管理** — 多版本隔离、BMCLAPI 版本列表、一键安装/删除
- 🔧 **ModLoader 安装** — Fabric / Forge / NeoForge / Quilt 一键安装
- 🎮 **Mod 管理** — CurseForge + Modrinth 双源，搜索/下载/启用禁用/配置编辑
- 🗂️ **实例系统** — 创建/导入/导出游戏实例，独立管理 Mod 和配置
- 🔗 **P2P 实例分享** — WebRTC 直连技术，6 位分享码一键分享
- 🎨 **主题自定义** — 色盘编辑器，自定义主题配色方案
- ⌨️ **全局快捷键** — 自定义全局快捷键，快速启动游戏
- 💥 **崩溃分析** — 游戏崩溃自动捕获并解析崩溃报告（10 类崩溃特征识别）
- 🔄 **自动更新** — 独立版本更新页，GitHub Releases 检测、可取消下载、一键安装
- 🗄️ **数据备份** — 支持实例数据备份与恢复，安全可靠

## 📋 版本历史

| 版本 | 日期 | 主要变更 |
|------|------|---------|
| **v0.7.3 质量批次** | 2026-10-11 | i18n 词条修复（相对时间键名、中英差异键）、schema 冲突修复、tsc 类型修复、单元测试 278/278 全绿、样式死代码清理 |
| **v0.7.3** | 2026-09-26 | 独立版本更新页（发布说明渲染、取消下载、进度速度）、水波纹横幅、检查更新双链路仲裁 |
| **v0.7.2** | 2026-09-26 | 更新检查改为 GitHub API 版本对比双链路，检查结果全反馈、12 秒超时恢复 |
| **v0.7.1** | 2026-09-26 | 崩溃分析系统、XMCL 启动核心、Java 自动选择、ModLoader/Mod 生态、Lumin UI/UX 设计系统、i18n 全面补全 |
| **v0.6.4** | 2026-07-17 | macOS 双架构构建支持（ARM64 / x64）、账户管理流程优化、Node.js 24 LTS |
| **v0.6.2** | 2026-07-04 | Design Token 设计体系、磨砂玻璃 UI 效果、启动画面优化（版本号动态注入）、HomePage 重构 |
| **v0.6.1** | 2026-07-02 | 启动稳定性修复（JVM 参数、进程独立运行）、下载可靠性增强（重定向、文件校验）、资源下载源优化 |
| **v0.6.0** | 2026-06-28 | UI 架构重构（设置页分类拆分、`.vox-*` 控件统一、主题系统重构） |
| **v0.5.5** | 2026-06-25 | i18n 国际化全面接入、TypeScript 类型修复、UI/UX 优化、ModLoader 安装完善 |
| **v0.5.4** | 2026-06-20 | 架构优化（Squirrel 安装器、启动器统一、watcher）、性能优化、Bug 修复 |
| **v0.5.3** | 2026-06-09 | 全局快捷键系统、通知系统增强、版本列表双层缓存、骨架屏优化 |
| **v0.5.2** | 2026-06-07 | P2P 实例分享（WebRTC）、主题自定义（色盘编辑器）、虚拟列表优化 |
| **v0.5.0** | 2026-06-05 | 启动器热更新、多镜像下载、智能 Java 版本匹配、下载管理页面 |
| **v0.4.3** | 2026-06-04 | 启动核心修复、类路径传递修复、Forge 模块系统参数修复 |
| **v0.4.2** | 2026-06-02 | ESLint v9 配置、安全配置模板、日志级别修正 |
| **v0.3.1** | 2026-05-19 | 自定义域名支持、文档网站全面升级 |
| **v0.3.0** | 2026-04-28 | Mod 配置编辑 UI、实例导入/导出、全局下载进度弹窗 |
| **v0.2.0** | 2026-04-26 | CurseForge + Modrinth 双源下载、崩溃监控、皮肤管理 |
| **v0.1.0** | 2026-04-24 | 首个公开版本，微软登录、版本管理、ModLoader 安装 |

## 🛠️ 技术栈

| 层级 | 技术 | 版本 |
|------|------|------|
| 桌面框架 | Electron | 42.6+ |
| 前端框架 | Vue 3 + Composition API | 3.5+ |
| 构建工具 | Vite + electron-vite | 8.1+ / 5.0+ |
| 语言 | TypeScript | 5.5+ |
| UI 样式 | SCSS + CSS Variables（Design Token 像素风设计系统） | - |
| 状态管理 | Pinia | 2.2+ |
| 路由 | Vue Router | 4.4+ |
| 启动核心 | @xmcl/* 工具链 | 2.x / 3.x / 6.x |
| 数据库 | better-sqlite3 | 12.0+ |
| 日志 | electron-log | 5.0+ |
| 运行时要求 | Node.js | 24+ |

## 📋 支持平台

| 平台 | 状态 | 架构 |
|------|------|------|
| Windows 10+ | ✅ 已支持 | x64 |
| macOS | ✅ 已支持 (CI) | x64 / arm64 |
| Linux | ⏳ 计划中 | x64 |

## 🚀 本地开发

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run docs:dev

# 构建生产版本
npm run docs:build

# 预览构建结果
npm run docs:preview
```

## 📄 协议

本项目基于 [MIT 协议](https://github.com/MeowY-Studios/VoxVer-Launcher/blob/main/LICENSE) 开源。

> Minecraft 是 Microsoft Corporation 的商标。本项目与 Mojang Studios 或 Microsoft 无关。

## 👤 作者

**nnkmn (EccenTri)** — [GitHub](https://github.com/nnkmn)
