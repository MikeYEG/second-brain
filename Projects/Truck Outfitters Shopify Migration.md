---
type: project
status: active
tags: [40two, shopify, client-work]
updated: 2026-09-18
---


# Truck Outfitters Shopify Migration

Build a new Shopify theme for [[Truck Outfitters]] that closely matches their existing WooCommerce site (eagletruckaccessories.com), plus a custom sync app.

## Scope
Two quotes sent via quotes.40two.ca:
1. **AIMS-to-Shopify Sync Tool** — custom app doing a nightly inventory / pricing / fitment sync from AIMS.
2. **Store migration** — 451 products @ $4, 60 collections, 8 support hours.

Terms: 25% deposit on the custom app work and 25% deposit on the Shopify work.

## Requirements
- Automotive parts store → needs a Year/Make/Model vehicle fitment filter like the current WooCommerce site.
- Theme should stay close to the current WooCommerce look.

## Current state
- **Sync tool: LIVE.** Kit `0300e7c` deployed to `C:\AIMS-Sync` on the AIMS server 2026-09-13; first sync created 362 Eagle products on the new store (51wnwt0m); nightly task `AIMS Shopify Sync (eagle)` at 23:00. Export read from `E:\aims\ver72\aims-interface\website.new\webexport`. Products have no images yet (none on the server) — see Open questions.
- **Kit `2026.09.18-06` built and signed, NOT yet installed** (2026-09-18, from `49289b3`, `master` pushed). Carries the actionable Slack message ([[2026-09-18 Sync alerts name the exact fix]]) and a `setup validate` disk-space check. Server still runs `2026.09.18-04`; rollback copy of `-04` kept in `E:\Github Repos\AIMStoShopify-kits\`.
- **Watch on the first image night:** an update carrying `files` must not duplicate media; an update without must not clear it (§15 of the runbook).
- **Store migration / theme:** kickoff held Sep 2026.

## Open questions
- Should stock quantities from AIMS be displayed on the Shopify storefront? (raised at kickoff)
- Should a nightly run with zero uploadable images count as a failure? (today: counted + warned, exit 0)
- Spec §20 questions for the AIMS consultant: regeneration of `full-<supplier>.csv` when supplier data changes; image folders named exactly as each sheet's `folder:` line.
- When is an image Shopify refused sent again? The runbook doesn't settle it, so the Slack message only claims "a replaced file is sent on the next run".
- `imageMissing` counts a shared family image once per part (53 counted vs 39 distinct files on the test fixture) — leave, or count files?
- Eagle's 5 attribute conflicts are still open in AIMS; the new message names the rows — send Kalie the first night's message.

## Links
[[Truck Outfitters]] · [[40Two]] · [[40Two Standard Quote Terms]]

## Log
- 2026-09 — Quotes sent; kickoff.
- 2026-09-11/12 — Sync tool rewritten for the new AIMS export (config-driven layout, server-side images, `validate` proves the config files against real headers); e2e dry run 363 creates; merged + pushed. Decision: [[2026-09-11 AIMS export layout lives in config files]].
- 2026-09-13 — GO-LIVE: kit 0300e7c on the AIMS server, 362 products created, nightly task scheduled 23:00. Images pending (WinSCP seed of 223 from accessorywarehouse.ca; 209 need WCS). Decision: launch without images.
- 2026-09-14 — Products were unpublished: built publish-on-create + `publish` catch-up, and Slack notifications per store; merged Mike's two fixes; kit 2e89a5f signed (1069 tests). Deploy + push pending.
- 2026-09-18 — Slack message rebuilt to say exactly what to fix (part, export file, AIMS column, values, the change); `unmatched` demoted from the alerting counters. Commit `3f90fa1` (+ disk-space check `8171584`, guide `49289b3`), all pushed; kit `2026.09.18-06` signed, 1285 tests. Install pending. Decision: [[2026-09-18 Sync alerts name the exact fix]].
