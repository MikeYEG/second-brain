---
type: decision
date: 2026-09-11
project: "[[Truck Outfitters Shopify Migration]]"
status: accepted
updated: 2026-09-12
---

# AIMS export layout lives in config files

## Context
On 2026-09-11 the AIMS server started writing a new export: one `full-<supplier>.csv` per supplier (one row per fitment, all suppliers), a family sheet and an image sheet per supplier, and the image files themselves in folders beside the sheets. The old five-file format (`master-<suffix>.csv`, `category-map.json`, images fetched from accessorywarehouse.ca) is dead. Mike expects the layout to change again and more stores to follow Eagle.

## Decision
- Format facts live in config, not code: `export-format.json` (server-level — which files, which columns play which roles, wildcard columns, stale rule) and `store-<key>.json` (per store — brand filter, title template, body sections, metafield lists, Product Destination → collection handles). Roles are fixed in code; everything else is editable and `setup validate` proves both files against the real headers and parts.
- One Shopify product per AIMS part; a store carries every part whose Brand matches its rules file (Eagle Manufacturing: 375 parts, 363 priced).
- Images are uploaded by the sync from the server folders through Shopify staged uploads; no web host is ever fetched.

## Alternatives considered
- Hard-coding the new layout (rejected — the next change would be another rewrite).
- Keeping category-map.json beside a new format file (rejected — one per-store file is the natural home for brand, titles and categories together).
- Keeping accessorywarehouse.ca as the image source (rejected — it serves the old file names behind Cloudflare and would leave a web dependency in a nightly job).

## Consequences
- An AIMS column rename is an edit to `export-format.json` plus `AimsSync setup validate`, not a code change.
- A new store is `setup map` (brand prompt seeds `store-<key>.json` from the Eagle template) plus editing its categories.
- The spec's title example for universal parts renders with a comma (`MS LED Light Bar, 20" inch`) — the template is config and can be changed without code.
- Implemented on `feature/new-export-format`, merged 2026-09-12 (`0300e7c`).
