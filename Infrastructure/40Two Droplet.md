---
type: infrastructure
status: active
tags: [40two, digitalocean, docker]
updated: 2026-09-03
---


# 40Two Droplet

DigitalOcean droplet `40two-droplet-1` hosting the [[40Two]] self-hosted stack. Run as root.

## Layout
- `/opt/40two-stack` — single `docker-compose.yml`; dirs `caddy/`, `nginx/`, `vaultwarden-data/`
- Per-service env files: `.env.<service>` (e.g. `.env.leantime`)
- Caddy fronts everything

## Services
| Service | URL | Notes |
|---|---|---|
| Invoice Ninja | quotes.40two.ca | Quotes/invoices; built-in approval/signature |
| Vaultwarden | passwords.40two.ca | Self-hosted Bitwarden |
| Keeper | calendar.40two.ca | keeper.sh calendar sync |
| QBO MCP server | qbo.mcp.40two.ca | FastMCP in Docker, compose service `qbomcp`; Claude sign-in via 40Two Entra ID app "Claude MCP – QuickBooks"; Intuit dev app "40Two MCP" on production keys, connected to 40Two Group Inc. |
| Leantime | — | Planned |

Email via Resend SMTP.

## Access
Credentials live in Vaultwarden and the `.env.<service>` files on the host — never in this vault.

## Maintenance
- Auto-updates monthly, mid-month (cron on the 15th).
- Covered by the weekly server health check — see [[Scheduled Briefs]].

## Links
[[Claude Integrations]]
