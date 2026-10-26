---
title: "贡献指南"
---

# 贡献指南

欢迎为 VoxVer Launcher 提交 Issue 或 Pull Request。提交前请先跑通本地检查，保持改动范围聚焦。

## 命名约定

| 类型 | 规范 | 示例 |
|------|------|------|
| 文件 / 目录 | kebab-case | `game.launcher.service.ts` |
| 类 / 接口 / 类型 | PascalCase | `GameLauncherService` |
| 函数 / 变量 | camelCase | `startGame()` |
| 常量 | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT` |

## 代码检查

```bash
# ESLint
npm run lint

# Prettier
npm run format

# 类型检查（web / node 双配置）
npx tsc --noEmit -p tsconfig.web.json
npx tsc --noEmit -p tsconfig.node.json
```

## 测试

```bash
# 运行全部单元测试（Vitest）
npm test

# 监听模式
npm run test:watch

# 覆盖率
npm run test:coverage
```

::: warning 注意
提交前请确保 `npm test` 与双配置 `tsc` 均为通过状态，避免把类型错误或失败用例带进主分支。
:::

## 提交 Pull Request

1. Fork 仓库并从 `main` 拉出功能分支
2. 改动尽量聚焦单一目的，避免混入无关格式化
3. 写清变更原因与影响范围，附上复现步骤或截图
4. 确认 CI 通过后提交 PR，等待维护者评审

## 相关文档

- [开发指南](/dev/) — 环境准备、构建与依赖说明
- [架构说明](/dev/architecture) — 分层、IPC、数据库与认证流程
- [更新日志](/guide/changelog) — 各版本变更记录
