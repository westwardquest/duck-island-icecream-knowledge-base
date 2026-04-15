# duck-island-icecream-knowledge-base

Knowledge-only repository for **Duck Island Icecream** (nested under the workspace clone). Add Markdown under `knowledge/` — use `knowledge/business/` for customer-facing docs and `knowledge/technical/` for internal docs. GitHub webhook `push` → `https://extreme-development-framework.vercel.app/api/webhooks/github` (quickstart may create it with `--push`; otherwise from the framework repo: `node scripts/quickstarts/create-knowledge-webhook.mjs` with this workspace as cwd or first arg).
