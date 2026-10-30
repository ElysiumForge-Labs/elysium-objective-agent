# elysium-objective-agent

Objective-driven agent dashboard for ElysiumForge Labs: users sign in, hand an objective to an agent, and follow the run — chat, step progress, documents, and an admin view.

Part of [ElysiumForge Labs](https://github.com/ElysiumForge-Labs).

> **Independent research repository.** Not affiliated with, endorsed by, or sponsored by Kinetiq or Hyperliquid. Use throwaway credentials for local and staging runs. Never commit production secrets.

## Features

- Sign-in and session management
- Objective submission and agent run orchestration
- Live chat and step-progress views
- Document and artifact surfaces for run outputs
- Admin view for operators
- Typed end-to-end API via tRPC

## Stack

| Layer | Technology |
| --- | --- |
| Client | React 19, Vite, TanStack Query, Radix UI |
| Server | Express, tRPC |
| Data | Drizzle ORM, MySQL (or TiDB) |
| Auth | Manus OAuth |
| Tests | Vitest |
| Package manager | pnpm |

## Getting started

### Prerequisites

| Program | Version |
| --- | --- |
| Node.js | 22.x+ |
| pnpm | 10.x+ |
| MySQL | 8.0+ (or TiDB) |

### Install and run

```bash
pnpm install
cp .env.example .env.local   # fill auth, DB, and model settings
pnpm db:push
pnpm dev
```

| Command | Purpose |
| --- | --- |
| `pnpm install` | Install dependencies |
| `pnpm dev` | Local development server |
| `pnpm test` | Vitest suite |
| `pnpm check` | Typecheck |
| `pnpm db:push` | Generate and apply database migrations |
| `pnpm build` | Build client and server |
| `pnpm start` | Run production build |

Local setup, environment variables, and troubleshooting: [docs/guides/setup.md](docs/guides/setup.md).

## Layout

```
client/     React app
server/     API, auth, and the agent runtime
shared/     Types shared by client and server
drizzle/    Schema and migrations
docs/       Guides, deployment, and reference
scripts/    Deploy helpers
```

Framework code lives in `server/_core`. Product procedures are in `server/routers.ts` and feature modules (`agent*`, `fileUpload*`, `google*`).

## Documentation

Start at [docs/README.md](docs/README.md).

## Security

- Keep `.env.local` out of version control.
- Prefer throwaway OAuth apps and API keys for local work.
- Review deployment manifests (`railway.json`, `render.yaml`, `Dockerfile`) before pointing them at production credentials.
