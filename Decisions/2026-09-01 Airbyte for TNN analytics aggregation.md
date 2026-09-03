---
type: decision
status: accepted
date: 2026-09-01
project: "[[TNN Analytics Warehouse]]"
updated: 2026-09-03
---


# Airbyte for TNN analytics aggregation

## Context
Needed a free or near-free way to pull GA4 (15 properties), Search Console, social, YouTube, and podcast downloads (Spotify, Acast) into one queryable store.

## Decision
Self-hosted Airbyte into Postgres, with Metabase on top, on a new droplet in TNN's DigitalOcean account.

## Consequences
Ops burden sits with Mike; cost is the droplet only. Warehouse becomes queryable by Claude once a Postgres MCP server is added.
