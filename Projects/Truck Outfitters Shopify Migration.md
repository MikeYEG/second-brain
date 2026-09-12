---
type: project
status: active
tags: [40two, shopify, client-work]
updated: 2026-09-12
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
- **Sync tool:** rewritten for the new AIMS export format and merged to `master` 2026-09-12 (`0300e7c`, 863 tests). One `AimsSync.exe` (setup wizard + nightly sync), kit = exe + `export-format.json` + `store-eagle.json` + 2 docs. Deployment home on the AIMS server is `C:\AIMS-Sync`; nothing has run there yet.
- **Go-live gates:** first supervised live sync on the new store (51wnwt0m) — media behaviour on `productSet` with/without `files`; the Shopify-side prerequisites from Sep 8–10 (cab-size list metafield, custom app, bed-accessories collection).
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
