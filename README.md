# elysium-objective-agent

Objective-driven agent product: users sign in, hand an objective to an agent, and follow the run from a dashboard — chat, step progress, documents, and an admin view.

Part of [ElysiumForge Labs](https://github.com/ElysiumForge-Labs).

> **Independent research repository.** Not affiliated with, endorsed by, or sponsored by Kinetiq or Hyperliquid. Use throwaway credentials for local and staging runs.

## Stack

| Layer | Technology |
| --- | --- |
| Client | React 19, Vite |
| Server | Express, tRPC |
| Data | Drizzle ORM, MySQL |
| Auth | Manus OAuth |

## Commands

From the project root (pnpm):

| Command | Purpose |
| --- | --- |
| `pnpm install` | Install dependencies |
| `pnpm dev` | Local server |
| `pnpm test` | Vitest |
| `pnpm check` | Typecheck |
| `pnpm db:push` | Generate and apply database migrations |
| `pnpm build` | Build client and server |
| `pnpm start` | Run production build |

Local setup, environment variables, and troubleshooting: [docs/guides/setup.md](docs/guides/setup.md).

## Layout

```
client/     React app
server/     API, auth, and the agent
shared/     Types used by client and server
drizzle/    Schema and migrations
docs/       Guides, deployment, and reference
scripts/    Deploy helpers
```

Framework code lives in `server/_core`. Product procedures are in `server/routers.ts` and feature modules (`agent*`, `fileUpload*`, `google*`).

## Documentation

Start at [docs/README.md](docs/README.md).
