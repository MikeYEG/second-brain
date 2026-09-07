---
type: infrastructure
status: active
tags: [vercel, supabase, hosting, costs]
updated: 2026-09-07
---

# Vercel and Supabase

## What it is
Mike's personal Vercel team ("mikeyeg's projects", Hobby, $0) hosting side projects, plus a Supabase Pro org billed through the Vercel Marketplace. Separate from the [[The Nation Network]] Vercel team (Pro + on-demand), which Mike administers but does not pay for personally.

## Services
- Vercel Hobby team — 11 projects: waffle-house-board, accountatlas, v0-rfp-management-platform, ninichoco, storefront-calculator, isb-core, next-l11, v0-get-account-gauge-com, allcanadiansportsbetting, tournamentcaddy, isb-tree-density-public.
- Supabase Pro org (via Vercel Marketplace) — 6 projects: allcanadiansportsbetting, GetAccountGauge.com, TournamentCaddy, L11, RFPStudio (active); showcade (paused). Every active project runs a Micro instance (~$10/mo); the plan's $10 credit covers one.
- v0 Premium — $20/mo (+GST), billed on the 13th.
- Domains on Vercel — tournamentcaddy.com, rfphive.com, ralphhr.com, mikesguideto.com ($11.25/yr each).

## Access
Vercel and Supabase MCP connectors in Claude (personal scope — cannot see the Nation Network team's invoices). Receipts arrive from invoice+statements@vercel.com to mike@infinitysquared.net.

## Maintenance
- Cost baseline (2026-09-07 review, USD incl. GST): Supabase ~$87/mo Apr–Aug (7 Micro instances; now 5 active → ~$68/mo expected), v0 $21/mo, domains ~$47/yr. Total ~$108/mo.
- All five active Supabase DBs had no user sign-in since 2026-06-01; GetAccountGauge has 0 users / 0 tables. Pausing the idle ones saves ~$42/mo; dropping to Free saves ~$68/mo but restores the 7-day auto-pause.
- v0 Premium appears orphaned — "out of credits on v0 Free plan" emails (Aug 4, Aug 18) while Premium is paid; check which workspace holds the subscription.
- Nation Network on-demand tracking ~$1,250/mo (Edge Requests + ISR Writes ≈ half); levers: longer ISR revalidate / on-demand revalidation, image minimumCacheTTL, log-drain sampling. Jul 21 payment failure on card •0584 — confirm whose card.

## Log
- 2026-09-07 — Cost review of Vercel + Supabase from receipts and live API data; recommendations above, nothing changed yet.
