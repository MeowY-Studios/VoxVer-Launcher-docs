---
title: "Developer Guide"
---

# Developer Guide

This section is for developers and covers local development, build steps, project structure and architecture. Players who just want to use the launcher should read the [User Guide](/en/guide/).

## Quick Start

### Prerequisites

- **Node.js** 24+ (enforced by `engines`, aligned with the `@types/node ^24` baseline)
- **npm** 10+
- **Git** (latest)
- Windows 10+ (the only officially supported platform for now)

### Clone & Install

```bash
git clone https://github.com/MeowY-Studios/VoxVer-Launcher.git
cd VoxVer-Launcher
npm install
```

::: tip Dependency install note
The dependency tree currently has a peer version conflict between `vite@8` and `@vitejs/plugin-vue@5` (pre-existing; to be resolved by upgrading plugin-vue). If installation reports a peer conflict, use `npm install --legacy-peer-deps`.
:::

### Environment Configuration

To use the CurseForge API, create a `.env` file in the project root:

```ini
CURSEFORGE_API_KEY=your_api_key_here
```

Apply for a key at <https://console.curseforge.com/#/api-keys>.

### Development Mode

```bash
npm run dev
```

The launcher runs in development mode with hot reload in the renderer.

### Building Installers

```bash
# Windows (NSIS installer)
npm run build:win

# macOS
npm run build:mac

# Linux
npm run build:linux
```

Artifacts are written to the `build/` directory in the project root; the Windows installer is named `VoxVer Launcher Setup x.x.x.exe`.

::: warning Platform note
Build scripts remain in the repository, but only Windows installers are currently published. The macOS build CI workflow was removed in v0.7.5; macOS and Linux are both planned.
:::

## Tech Stack

| Layer | Technology | Version |
|-------|------------|---------|
| Desktop framework | Electron | 42.6.1 |
| Frontend framework | Vue 3 + Composition API | 3.5.0 |
| Build tooling | Vite + electron-vite | 8.1.3 / 5.0.0 |
| Language | TypeScript | 5.5.0 |
| UI styling | SCSS + CSS Variables | Pixel design system |
| State management | Pinia | 2.2.0 |
| Router | Vue Router | 4.4.0 |
| Launch core | `@xmcl/*` toolchain | 2.x / 3.x / 6.x |
| Database | better-sqlite3 | 12.0.0 (ABI 146, bound to Electron) |
| Logging | electron-log | 5.0.0 |
| i18n | vue-i18n | 9.14.5 |
| Testing | Vitest + @vue/test-utils | 4.1.10 / 2.4.6 |

## Next Steps

| Document | Content |
|----------|---------|
| [Architecture](/en/dev/architecture) | Process layers, IPC channels, database, auth flow and design principles |
| [Contributing](/en/dev/contributing) | Naming conventions, linting, tests and PR workflow |
| [User Guide](/en/guide/) | Installation and usage docs for players |
