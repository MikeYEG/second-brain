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
- Supabase org (via Vercel Marketplace) — **Free plan since 2026-09-07**; 2 projects remain: supabase-TournamentCaddy (olqzftmpavhpgmcxvhyb, us-east-1, active dev — Stripe Connect/auctions, pg_cron) and supabase-L11 (tckbvzmyyezctwjedjsw, us-east-1, dormant since Jun). Free = 2 active projects max, no daily backups, auto-pause after 7 idle days, 90-day restore window once paused. Deleted 2026-09-07: showcade (never exported), allcanadiansportsbetting, GetAccountGauge.com, RFPStudio (all three in the export zip).
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
- 2026-09-07 — Org downgraded to Free; 4 projects deleted, 2 kept. Open: keep-alive for the two Free projects vs. accept auto-pause; idea floated of moving L11/TournamentCaddy DBs to the NHL Fantasy DO droplet.
- 2026-09-07 — Logical export of all 5 active Supabase projects (schema.sql + data.sql + checksums per project, restore-tested) delivered as `supabase-export-2026-09-07.zip` via Cowork. Not in the vault. showcade (paused) not exported. TournamentCaddy has fresh migrations (024–030, Sep 2–3) — treat as active, not idle. v0: Premium renews Sep 13; $51 purchased credit needs a paid plan to spend (refund via vercel.com/help).
