---
type: project
status: active
tags: [tnn, shopify, theme]
updated: 2026-09-04
---

# Nation Experiences Shopify Theme

Restyle the Nation Experiences store (nationexperiences.ca, [[The Nation Network]] fan-travel brand, currently Dawn) to look like contiki.com/en-ca. Work happens in the theme repo `40Two-ca/tnn-shopifytheme-nationexperiences`; `main` is linked to a demo store, so pushes land there directly.

## Current state
First pass shipped 2026-09-04 on Shopify Horizon 4.1.5: Contiki-style tokens (Archivo 900 headings, Jost body, one accent colour = palette colour 1, pill buttons), trip-card blocks driven by `custom.*` metafields or `badge:` / `duration:` tags, new home sections (trip finder, feature tiles, testimonials, destination tiles, book-with-confidence, partner logos), rebuilt header/footer/home/collection/product templates. Review and merchant to-do list in `docs/contiki-review.md` in the repo. Theme check clean; not yet eyeballed on the demo store.

## Open questions
- Store still needs: dark wordmark for the white header, hero + tile photos, `main-menu` / `footer` menus, partner logos, and the `custom.*` product metafield definitions.
- Accent shipped as volt green (`#D2FF28`); confirm with the team or swap in one setting.

## Links
[[The Nation Network]] · [[40Two]]

## Log
- 2026-09-04 — Reviewed Contiki, rebuilt the theme (3 commits), pushed to main.
