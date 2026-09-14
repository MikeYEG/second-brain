---
type: project
status: active
tags: [40two, shopify, client-work]
updated: 2026-09-13
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
- **Watch on the first image night:** an update carrying `files` must not duplicate media; an update without must not clear it (§15 of the runbook).
- **Store migration / theme:** kickoff held Sep 2026.

## Open questions
- Should stock quantities from AIMS be displayed on the Shopify storefront? (raised at kickoff)
- Should a nightly run with zero uploadable images count as a failure? (today: counted + warned, exit 0)
- Spec §20 questions for the AIMS consultant: regeneration of `full-<supplier>.csv` when supplier data changes; image folders named exactly as each sheet's `folder:` line.

## Links
[[Truck Outfitters]] · [[40Two]] · [[40Two Standard Quote Terms]]

## Log
- 2026-09 — Quotes sent; kickoff.
- 2026-09-11/12 — Sync tool rewritten for the new AIMS export (config-driven layout, server-side images, `validate` proves the config files against real headers); e2e dry run 363 creates; merged + pushed. Decision: [[2026-09-11 AIMS export layout lives in config files]].
- 2026-09-13 — GO-LIVE: kit 0300e7c on the AIMS server, 362 products created, nightly task scheduled 23:00. Images pending (WinSCP seed of 223 from accessorywarehouse.ca; 209 need WCS). Decision: launch without images.
