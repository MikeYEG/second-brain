---
type: infrastructure
status: idea
tags: [tnn, digitalocean, airbyte, metabase, mcp]
updated: 2026-09-10
---


# TNN Analytics Droplet

Planned DigitalOcean droplet (Toronto, Ubuntu 24.04, 4 vCPU / 8 GB / 160 GB, ~$48/mo) in TNN's DO account running the analytics stack for [[TNN Analytics Warehouse]]. Not yet created as of 2026-09-10.

## Services
- Airbyte OSS via `abctl` (Kubernetes-in-Docker) on host port 8000, behind Caddy at `airbyte.<host>`
- Docker Compose: Caddy (TLS for 3 hostnames), Postgres 16 (`warehouse` + `metabase_app` DBs), Metabase at `metabase.<host>`, warehouse MCP server (FastMCP) at `mcp.<host>/mcp`
- Cron (installed by bootstrap): 03:15 `pg_dumpall` to `/opt/backups` (14 days), 07:30 `ops/freshness-check.sh` to Slack, 04:00 on the 15th Airbyte + compose update

## Security
- DO Cloud Firewall 22/80/443 only is the boundary (Docker bypasses ufw). Postgres 5432 and Airbyte 8000 never exposed.
- Google OAuth client shared by the MCP server and Metabase Google Sign-In; Airbyte admin only.
- Secrets live in `/opt/tnn-analytics/.env`, `airbyte/.env.airbyte`, `airbyte/secrets/google-service-account.json` on the droplet (all git-ignored). Never in the vault.

## Code
`MikeYEG/tnn-analytics` (private) — `bootstrap.sh` builds the whole box; to move to the TNN org repo once verified.

## Log
- 2026-09-03: stack designed and packaged.
- 2026-09-10: build order set; droplet still to be created.
