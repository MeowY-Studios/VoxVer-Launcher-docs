---
title: "Contributing"
---

# Contributing

Contributions via Issues and Pull Requests are welcome. Run the local checks before submitting and keep each change focused.

## Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Files / directories | kebab-case | `game.launcher.service.ts` |
| Classes / interfaces / types | PascalCase | `GameLauncherService` |
| Functions / variables | camelCase | `startGame()` |
| Constants | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT` |

## Code Checks

```bash
# ESLint
npm run lint

# Prettier
npm run format

# Type checking (web / node configs)
npx tsc --noEmit -p tsconfig.web.json
npx tsc --noEmit -p tsconfig.node.json
```

## Tests

```bash
# Run all unit tests (Vitest)
npm test

# Watch mode
npm run test:watch

# Coverage
npm run test:coverage
```

::: warning Note
Make sure both `npm test` and the two `tsc` configurations pass before submitting, so type errors and failing cases do not reach `main`.
:::

## Submitting a Pull Request

1. Fork the repository and branch off `main`
2. Keep the change focused on one purpose; avoid unrelated formatting churn
3. Explain why the change is needed and its impact, with reproduction steps or screenshots
4. Confirm CI passes, then open the PR for review

## Related Documents

- [Developer Guide](/en/dev/) — environment setup, builds and dependencies
- [Architecture](/en/dev/architecture) — layers, IPC, database and auth flow
- [Changelog](/en/guide/changelog) — release history
