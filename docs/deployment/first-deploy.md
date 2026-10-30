# Elysium Agent — First Deployment

This guide walks through a first deploy to Render. Allow about 15 minutes, plus 5–10 minutes for the initial build.

## Before you start

- A Git hosting account, with this project pushed to a remote repository
- A [Render](https://render.com) account that can read that repository
- Manus project values for the environment variables in step 4

## 1. Publish the code

From the project root:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <repository-url>
git push -u origin main
```

If the repository already has a remote, skip `git init` and push the current branch instead.

## 2. Create the web service

1. Open [Render](https://render.com) and sign in.
2. Choose **New +** → **Web Service**.
3. Connect the repository and select `elysium-agent`.

| Field | Value |
| --- | --- |
| Name | `elysium-agent` |
| Environment | Node |
| Build command | `pnpm install && pnpm build` |
| Start command | `pnpm start` |
| Plan | Free |

Create the service. The build log should end with a live status. That usually takes 5–10 minutes.

## 3. Add environment variables

In the service, open **Environment** and add:

| Key | Value |
| --- | --- |
| `NODE_ENV` | `production` |
| `JWT_SECRET` | A long random string |
| `VITE_APP_ID` | Manus app id |
| `OAUTH_SERVER_URL` | `https://api.manus.im` |
| `VITE_OAUTH_PORTAL_URL` | `https://auth.manus.im` |

Copy `VITE_APP_ID` and `JWT_SECRET` from the Manus project settings. Placeholder values are enough to confirm the service boots; sign-in requires the real Manus values.

Save the variables. Render restarts the service automatically.

## 4. Verify

1. Copy the service URL from the top of the Render service page. It is typically `https://elysium-agent.onrender.com`.
2. Open it and confirm the sign-in page.
3. Sign in and check the dashboard, task creation, file upload, and documents.

## After deploy

- Share the service URL with people who should use the platform.
- Rename the service or attach a custom domain from the Render service settings.
- Move off the free plan when you need a database with more storage or a service that does not sleep.

## Troubleshooting

| Symptom | Action |
| --- | --- |
| Build failed | Retry the deploy. Confirm Node.js 18 or later and that `pnpm install` and `pnpm build` succeed locally. |
| Cannot connect to the database | Add `DATABASE_URL` under **Environment**. The app can start without it, but data features will not. |
| Sign-in fails | Recheck `VITE_APP_ID`, `OAUTH_SERVER_URL`, and `VITE_OAUTH_PORTAL_URL`. |
| 404 after deploy | Wait until the service status is live, then refresh. |

Service logs are under **Logs** on the Render service page.

## Cost

The free web service is $0. A paid web service is about $7 per month, and a starter database is about $15 per month, if you outgrow the free limits.

## Related documents

- `docs/deployment/quick-start.md` — short version of this deploy
- `docs/deployment/production.md` — database, custom domain, and maintenance
- `docs/guides/setup.md` — local setup
- `docs/deployment/overview.md` — production checklist
