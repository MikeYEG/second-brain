---
type: project
status: active
tags: [tnn, analytics, data]
updated: 2026-09-10
---


# TNN Analytics Warehouse

One queryable place for all of [[The Nation Network]]'s numbers: Google Analytics, Search Console, social account views, YouTube views, and podcast downloads across all properties, with Metabase dashboards and an MCP server so Claude can query it.

## Current state
- Spec and code complete, nothing deployed yet (as of 2026-09-10). Repo `MikeYEG/tnn-analytics` (private); `docs/SPEC.md` is the vision/scope/decisions document, `docs/RUNBOOK.md` the 14-phase deployment, `docs/PROPERTIES.md` the account inventory.
- Build order agreed: Day 1 approvals + Google Cloud + droplet; Day 2 GA4/GSC via `airbyte/provision.py`, SQL views, `metabase/provision.py`, Claude connector; owned-token sources over weeks 1-2; verify pass at two weeks; then move repo to the TNN org.

## Open items
- Kick off the approval-gated pieces: Acast Data Exports (email), Meta system-user token, LinkedIn Community Management API, TikTok app review.
- After first sync: settle `-- verify` column names in `sql/010_views.sql` and the two raw-table dashboard cards (send `000_inspect.sql` output to Claude).
- Confirm which podcasts are Spotify-hosted vs Acast (drives the monthly manual CSV list).
- Confirm Edmonton/Vancouver social handles post-rebrand (`dfoedmonton` / `dfovancouver` expected).
- Once the MCP connector is live: add a Nation Network pulse to the morning brief.
- Deferred candidates: Bluesky, Threads, Nation Gear Shopify orders, newsletters; revenue (Ad Manager, affiliate) and X out of scope.

## Decisions
- Self-hosted **Airbyte** for ingestion (free/near-free was the requirement) — [[2026-09-01 Airbyte for TNN analytics aggregation]]
- Runs on a new DigitalOcean droplet in TNN's DO account with **Postgres + Metabase** — see [[TNN Analytics Droplet]]
- Warehouse MCP server uses Google Workspace OAuth (FastMCP OAuth proxy) with a domain/email allow-list; read-only role, SELECT-only grammar.
- Dashboards and Airbyte connections are provisioned from code; UI edits get overwritten on re-run.
- Package lives in Mike's personal private repo `MikeYEG/tnn-analytics` for now; move to the TNN org repo once verified.
- Full decision table with alternatives: `docs/SPEC.md` section 5 in the repo.

## Facts
- 13 owned web properties (15 GA4 properties), 12 known YouTube channels (IDs in `docs/PROPERTIES.md`), Instagram + Facebook per brand, LinkedIn, TikTok.
- Podcasts hosted on Acast (automatic via S3 export) and Spotify for Creators (monthly manual CSV via Google Drive).
- Rebrand 2026-08-12: Oilersnation / FlamesNation / CanucksArmy / TheLeafsNation becoming Daily Faceoff Edmonton / Calgary / Vancouver / Toronto; site URLs unchanged until Jan 2027.

## Log
- 2026-09-02: scope, stack choice, package v1 (bootstrap, compose, SQL views, connector runbook), MCP server added, account inventory compiled.
- 2026-09-03: Metabase dashboard provisioner; Airbyte-as-code; freshness alert; Metabase Google Sign-In; repo created and docs (spec, runbook, properties) committed.
- 2026-09-10: day-by-day build order written; ready to deploy.

## Links
[[The Nation Network]] · [[TNN Analytics Droplet]] · [[Claude Integrations]]
