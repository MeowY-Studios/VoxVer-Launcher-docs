---
title: "架构说明"
---

# 架构说明

VoxVer Launcher 由 **Electron 主进程**（`electron/`）与 **Vue 渲染进程**（`src/`）两部分组成，业务能力集中在主进程的服务层，通过 IPC 通道暴露给界面。

## 进程分层

```
渲染进程 src/（Vue 3 + Pinia）
        │  window.api.xxx()  ← preload 暴露的 IPC 桥
        ▼
preload.ts（类型化桥接，30+ 通道）
        ▼
主进程 electron/
  ├── ipc/        通道处理器（20+ 模块，入参校验 + 调用服务）
  ├── services/   业务服务层（认证、下载、启动、Mod、实例…）
  ├── adapters/   平台/游戏适配器（接口 + Minecraft 实现 + 注册中心）
  ├── types/      IPC 与数据库类型定义
  └── utils/      日志、加密、哈希、平台探测
```

- **IPC 通道**：渲染进程不直接访问文件系统或网络，所有能力都经 `preload.ts` 暴露的通道调用主进程。
- **服务层**：单一职责，可独立测试；下载、启动、ModLoader 等复杂流程均在此层实现。
- **适配器层**：为不同加载器（Forge / NeoForge / Fabric / Quilt）与平台提供统一接口，新增实现无需改动调用方。

## 关键目录

```
electron/
├── main.ts                       # 主进程入口（窗口、生命周期、服务注册）
├── preload.ts                    # IPC 桥接
├── ipc/                          # account / config / crash / download / game /
│                                 # instance / java / mod / modloader / share /
│                                 # modpack / hotkey / theme / backup / updater /
│                                 # notification / window 等通道
├── services/                     # microsoft.auth / accounts / versions /
│                                 # modloader.service / modrinth.service /
│                                 # mod.service / skin.service / crash.service /
│                                 # xmcl.launcher.service / java.management.service /
│                                 # instances / database / download.service /
│                                 # backup.service / hotkey.service / theme.service
├── types/                        # ipc.types / database.types / modloader.types
└── utils/                        # logger / crypto / hash / platform

src/
├── pages/                        # 各功能页面（首页、账户、版本、设置、更新…）
├── components/                   # common（Px UI 组件库）/ download / instance / launch
├── stores/                       # Pinia 状态
├── styles/                       # pixel-ui.css、vox-controls.scss、themes/
└── locale/                       # zh-CN / en-US 语言包
```

## 数据库

使用 SQLite（better-sqlite3，WAL 模式），库文件位于 `userData/data/voxver.db`。

| 表名 | 用途 | 关键字段 |
|------|------|---------|
| `accounts` | 账户信息 | access_token（加密）、refresh_token、profile、type |
| `instances` | 游戏实例 | version、loader、game_dir、launch_args |
| `downloads` | 下载任务 | url、progress、status、file_path |
| `versions` | 版本缓存 | id、type、metadata、local_path |
| `configs` | 全局配置 | key-value（Java 路径、游戏目录、下载源策略等） |
| `share_history` | P2P 分享/接收历史 | type、share_code、status、instance_name |

崩溃记录以日志文件形式存储，不入库。

## 认证流程

使用微软官方 Device Code Flow，用户无需在启动器内输入密码：

```
点击「微软登录」
  → 请求设备码（POST /oauth20_token.srf）
  → 展示设备码 + microsoft.com/devicelogin 链接
  → 用户在浏览器输入设备码
  → 每 5 秒轮询 token
  → Access Token → Xbox Live → XSTS → Minecraft Bearer Token
  → 拉取 Minecraft Profile（用户名、UUID、皮肤 URL）
  → 写入数据库（token 使用 safeStorage 加密）
  → 后续自动刷新，无需重复登录
```

## 下载链路

下载服务（`download.service.ts`）统一管理并发、线程、限速与重试：

| 配置项 | 默认 | 说明 |
|--------|------|------|
| `maxConcurrent` | 4 | 同时下载任务数（2 / 4 / 6 / 8 / 12 / 16） |
| `maxThreadsPerFile` | 8 | 单文件分片线程数 |
| `speedLimit` | 0 | 限速（0 为不限速） |
| `maxRetries` | 5 | 分片失败重试次数 |
| `mirrorStrategy` | `auto` | `auto` / `official` / `mirror`，`shouldMirror` 按策略决定是否走镜像 |

自 v0.7.5 起，策略真实参与下载链路判断，不再只是界面开关。

## 架构设计原则

1. **务实优先** — 先跑通再优化，不追求过度设计
2. **类型安全** — TypeScript 严格模式，IPC 通道完整类型映射
3. **模块化** — IPC / 服务 / 前端分层，适配器模式支持多加载器与多平台
4. **即时反馈** — 每个耗时操作都有进度、状态与通知
5. **安全** — token 加密存储、不保存密码、API Key 走环境变量
6. **像素美学** — Press Start 2P 字体 + 暗色调 + 发光强调
7. **国际化** — 界面文本统一走 `$t()`，语言包放 `src/locale/`
8. **控件统一** — 全局控件使用 `.vox-*` 前缀，设计令牌使用 `--voxver-*` CSS 变量
