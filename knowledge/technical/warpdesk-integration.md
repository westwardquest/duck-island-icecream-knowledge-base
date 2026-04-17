# WarpDesk integration

## Configuration files

- **`warpdesk.config`** — Key/value lines consumed by quickstart scripts and by the ticket CLI for defaults (e.g. `WORKSPACE_SLUG`, `DEV_APP_ORIGIN`). This file is **gitignored**; do not commit secrets.
- **`.cursor/mcp.json`** — Defines the **`warpdesk-tickets`** stdio server: `node` + `tsx` running **`vendor/warpdesk-client-kit/mcp/src/index.ts`**, with **`cwd`** under the kit. **`WARPDESK_BASE_URL`** must match the deployment where the PAT was issued (no trailing slash). **`WARPDESK_PERSONAL_ACCESS_TOKEN`** must be a full **`wds_pat_…`** token from the app **Settings → Personal access tokens**.

Cursor does not enable MCP servers automatically: **Settings → Features → Model Context Protocol** → enable **`warpdesk-tickets`**.

## Ticket API from the terminal

Root **`package.json`** scripts delegate to **`vendor/warpdesk-client-kit/mcp/tickets-cli.mjs`**:

| Script | Purpose |
| ------ | ------- |
| `npm run warpdesk:tickets` | List tickets |
| `npm run warpdesk:tickets:queue` | Priority active queue |
| `npm run warpdesk:ticket -- <uuid>` | Single ticket |

Auth and base URL match MCP: token from env or `.cursor/mcp.json`; base URL from **`WARPDESK_BASE_URL`** or **`DEV_APP_ORIGIN`** in `warpdesk.config`. If MCP uses a different host than `warpdesk.config`, set **`WARPDESK_BASE_URL`** in the environment when running the CLI so calls hit the same deployment.

## MCP tools (typical)

Examples: **`list_tickets`**, **`get_ticket`**, **`list_priority_active_tickets`**, **`draft_ticket_update`**, **`search_tickets`**, **`bootstrap_workspace`**. Direct **`update_ticket`** / **`add_ticket_comment`** are off unless **`WARPDESK_MCP_ALLOW_DIRECT_UPDATES=1`** is set in MCP env.

## Ticket changes: draft-first

Agents should **not** post arbitrary ticket edits through the CLI for normal review workflows. Use **`draft_ticket_update`** (or the equivalent CLI draft command), which writes YAML under **`.edf/ticket-drafts/`** or **`.warpdesk/ticket-drafts/`** (see current kit). Humans **Confirm** or **Discard** in **WarpDesk Tools** so PATCH/comment runs only after review.

Public comments should stay **customer-facing**: clear and professional; avoid dumping stack traces or internal paths unless the customer asked for them.

## Git and pushes

Do **not** push to remotes unless the developer explicitly asked. Ticket work should live on a branch whose name includes the ticket number (e.g. **`ticket-3`**).
