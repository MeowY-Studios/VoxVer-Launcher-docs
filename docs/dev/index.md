---
title: "开发指南"
---

# 开发指南

本节面向开发者，介绍本地开发、构建流程、项目结构与架构设计。只想使用启动器的玩家请阅读 [用户指南](/guide/)。

## 快速开始

### 前置要求

- **Node.js** 24+（`engines` 约束，与 `@types/node ^24` 类型基线一致）
- **npm** 10+
- **Git** 最新版本
- Windows 10+（当前正式支持 Windows）

### 克隆与安装

```bash
git clone https://github.com/MeowY-Studios/VoxVer-Launcher.git
cd VoxVer-Launcher
npm install
```

::: tip 依赖安装提示
当前依赖树存在 `vite@8` 与 `@vitejs/plugin-vue@5` 的 peer 版本声明冲突（既有问题，待升级 plugin-vue 解决）。如安装报 peer 冲突，可使用 `npm install --legacy-peer-deps`。
:::

### 环境配置

如需使用 CurseForge API，在项目根目录创建 `.env` 文件：

```ini
CURSEFORGE_API_KEY=your_api_key_here
```

申请地址：<https://console.curseforge.com/#/api-keys>

### 开发模式

```bash
npm run dev
```

开发模式下启动器以开发模式运行，渲染进程支持热重载。

### 构建安装包

```bash
# Windows（NSIS 安装程序）
npm run build:win

# macOS
npm run build:mac

# Linux
npm run build:linux
```

产物输出到项目根目录的 `build/` 目录，Windows 安装包文件名为 `VoxVer Launcher Setup x.x.x.exe`。

::: warning 平台说明
构建脚本保留在仓库中，但当前只发布 Windows 安装包。macOS 构建的 CI 工作流已在 v0.7.5 移除，macOS / Linux 均处于计划中。
:::

## 技术栈

| 层级 | 技术 | 版本 |
|------|------|------|
| 桌面框架 | Electron | 42.6.1 |
| 前端框架 | Vue 3 + Composition API | 3.5.0 |
| 构建工具 | Vite + electron-vite | 8.1.3 / 5.0.0 |
| 语言 | TypeScript | 5.5.0 |
| UI 样式 | SCSS + CSS Variables | 像素风设计系统 |
| 状态管理 | Pinia | 2.2.0 |
| 路由 | Vue Router | 4.4.0 |
| 启动核心 | `@xmcl/*` 工具链 | 2.x / 3.x / 6.x |
| 数据库 | better-sqlite3 | 12.0.0（ABI 146，随 Electron 版本绑定） |
| 日志 | electron-log | 5.0.0 |
| 国际化 | vue-i18n | 9.14.5 |
| 测试 | Vitest + @vue/test-utils | 4.1.10 / 2.4.6 |

## 下一步

| 文档 | 内容 |
|------|------|
| [架构说明](/dev/architecture) | 进程分层、IPC 通道、数据库、认证流程与架构原则 |
| [贡献指南](/dev/contributing) | 命名约定、代码检查、测试与提交流程 |
| [用户指南](/guide/) | 面向玩家的安装与使用文档 |
