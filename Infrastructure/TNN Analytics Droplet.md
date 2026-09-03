---
type: infrastructure
status: active
tags: [tnn, digitalocean, airbyte]
updated: 2026-09-03
---


# TNN Analytics Droplet

New DigitalOcean droplet in TNN's DO account running the analytics stack for [[TNN Analytics Warehouse]].

## Services
- Airbyte (ingestion)
- Postgres (warehouse)
- Metabase (dashboards)
- Planned: Postgres MCP server for Claude, Google Workspace OAuth sign-in

## Code
`MikeYEG/tnn-analytics` (private) — to move to the TNN org repo once verified.
