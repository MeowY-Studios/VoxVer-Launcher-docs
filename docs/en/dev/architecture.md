---
title: "Architecture"
---

# Architecture

VoxVer Launcher consists of an **Electron main process** (`electron/`) and a **Vue renderer** (`src/`). Business logic lives in the main-process service layer and is exposed to the UI through IPC channels.

## Process Layers

```
Renderer src/ (Vue 3 + Pinia)
        │  window.api.xxx()  ← IPC bridge exposed by preload
        ▼
preload.ts (typed bridge, 30+ channels)
        ▼
Main process electron/
  ├── ipc/        channel handlers (20+ modules: validate input, call services)
  ├── services/   business services (auth, download, launch, mods, instances…)
  ├── adapters/   platform/game adapters (interface + Minecraft impl + registry)
  ├── types/      IPC and database type definitions
  └── utils/      logger, crypto, hash, platform probing
```

- **IPC channels**: the renderer never touches the filesystem or network directly; every capability is invoked through channels exposed by `preload.ts`.
- **Service layer**: single responsibility and independently testable; complex flows such as downloads, launching and ModLoader installs live here.
- **Adapter layer**: a unified interface for loaders (Forge / NeoForge / Fabric / Quilt) and platforms, so new implementations need no changes at call sites.

## Key Directories

```
electron/
├── main.ts                 # entry (windows, lifecycle, service registration)
├── preload.ts              # IPC bridge
├── ipc/                    # account / config / crash / download / game /
│                           # instance / java / mod / modloader / share /
│                           # modpack / hotkey / theme / backup / updater /
│                           # notification / window
├── services/               # microsoft.auth / accounts / versions /
│                           # modloader.service / modrinth.service /
│                           # mod.service / skin.service / crash.service /
│                           # xmcl.launcher.service / java.management.service /
│                           # instances / database / download.service /
│                           # backup.service / hotkey.service / theme.service
├── types/                  # ipc.types / database.types / modloader.types
└── utils/                  # logger / crypto / hash / platform

src/
├── pages/                  # feature pages (home, accounts, versions, settings, update…)
├── components/             # common (Px UI library) / download / instance / launch
├── stores/                 # Pinia state
├── styles/                 # pixel-ui.css, vox-controls.scss, themes/
└── locale/                 # zh-CN / en-US language packs
```

## Database

SQLite via better-sqlite3 in WAL mode; the file lives at `userData/data/voxver.db`.

| Table | Purpose | Key fields |
|-------|---------|------------|
| `accounts` | Account info | access_token (encrypted), refresh_token, profile, type |
| `instances` | Game instances | version, loader, game_dir, launch_args |
| `downloads` | Download tasks | url, progress, status, file_path |
| `versions` | Version cache | id, type, metadata, local_path |
| `configs` | Global config | key-value (Java path, game dir, download strategy…) |
| `share_history` | P2P share history | type, share_code, status, instance_name |

Crash records are stored as log files, not in the database.

## Authentication Flow

Microsoft Device Code Flow is used, so the user never types a password inside the launcher:

```
Click "Sign in with Microsoft"
  → request device code (POST /oauth20_token.srf)
  → show device code + microsoft.com/devicelogin
  → user enters the code in a browser
  → poll for token every 5 seconds
  → Access Token → Xbox Live → XSTS → Minecraft Bearer Token
  → fetch Minecraft profile (name, UUID, skin URL)
  → persist to database (token encrypted via safeStorage)
  → refresh automatically afterwards
```

## Download Pipeline

`download.service.ts` owns concurrency, threads, rate limiting and retries:

| Option | Default | Description |
|--------|---------|-------------|
| `maxConcurrent` | 4 | Parallel download tasks (2 / 4 / 6 / 8 / 12 / 16) |
| `maxThreadsPerFile` | 8 | Threads per file |
| `speedLimit` | 0 | Speed cap (0 = unlimited) |
| `maxRetries` | 5 | Retries per failed chunk |
| `mirrorStrategy` | `auto` | `auto` / `official` / `mirror`; `shouldMirror` decides per strategy |

Since v0.7.5 the strategy actually participates in download routing instead of being a UI-only switch.

## Design Principles

1. **Pragmatic first** — make it work, then refine; avoid over-engineering
2. **Type safety** — TypeScript strict mode with fully typed IPC channels
3. **Modularity** — IPC / service / UI layers, adapters for loaders and platforms
4. **Instant feedback** — progress, status and notifications for every long operation
5. **Security** — encrypted token storage, no passwords stored, API keys via env vars
6. **Pixel aesthetics** — Press Start 2P, dark palette, glow accents
7. **i18n** — all UI text goes through `$t()`, packs under `src/locale/`
8. **Consistent controls** — `.vox-*` prefixed controls, `--voxver-*` design tokens
