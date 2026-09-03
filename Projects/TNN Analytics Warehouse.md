---
type: project
status: active
tags: [tnn, analytics, data]
updated: 2026-09-03
---


# TNN Analytics Warehouse

One queryable place for all of [[The Nation Network]]'s numbers: Google Analytics, Search Console, social account views, YouTube views, and podcast downloads across all properties.

## Decisions
- Self-hosted **Airbyte** for ingestion (free/near-free was the requirement) — [[2026-09-01 Airbyte for TNN analytics aggregation]]
- Runs on a new DigitalOcean droplet in TNN's DO account with **Postgres + Metabase** — see [[TNN Analytics Droplet]]
- Package lives in Mike's personal private repo `MikeYEG/tnn-analytics` for now; move to the TNN org repo once verified.

## Facts
- 15 GA4 properties
- Podcasts hosted on Spotify and Acast

## Planned
- Postgres MCP server on the droplet so Claude can query the warehouse; Claude sign-in via Google Workspace OAuth.

## Links
[[The Nation Network]] · [[Claude Integrations]]
