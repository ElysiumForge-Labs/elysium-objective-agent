# Elysium Agent — Quick Start

Deploy the platform in about 15 minutes.

## Prerequisites

- A Git hosting account
- A [Render](https://render.com) account
- Node.js 18 or later, with `pnpm` installed locally if you publish from this machine

## 1. Publish the repository

From the project root:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <repository-url>
git push -u origin main
```

Replace `<repository-url>` with the remote you created for this project.

## 2. Create the Render service

1. Open [Render](https://render.com) and sign in.
2. Choose **New +** → **Web Service**.
3. Connect the repository and select `elysium-agent`.

| Setting | Value |
| --- | --- |
| Name | `elysium-agent` |
| Environment | Node |
| Build command | `pnpm install && pnpm build` |
| Start command | `pnpm start` |
| Plan | Free |

4. Create the web service and wait until Render reports that it is live. The first build usually takes 5–10 minutes.

## 3. Open the service

In the Render dashboard, copy the service URL and open it in a browser. A typical free-tier URL looks like `https://elysium-agent.onrender.com`.

After sign-in, confirm that you can:

- Create a task
- Upload a file
- View documents
- Open the admin panel if your account has that role

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| Build failed | Wait a few minutes and redeploy. Confirm Node 18+ and that `pnpm install` and `pnpm build` succeed locally. |
| Service will not connect | The first deploy may still be running. Check **Logs** on the service page. |
| Sign-in fails | Confirm the Manus environment variables in `docs/deployment/first-deploy.md`. |
| Page does not load | Refresh after the service status is **Live**. |

## Related documents

- `docs/deployment/first-deploy.md` — environment variables and a full first deploy
- `docs/deployment/production.md` — production settings, database, and custom domain
- `docs/deployment/overview.md` — checklist, Docker, and operations
