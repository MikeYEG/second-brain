---
type: project
status: active
tags: [tnn, shopify, theme]
updated: 2026-09-10
---

# Nation Experiences Shopify Theme

Restyle the Nation Experiences store (nationexperiences.ca, [[The Nation Network]] fan-travel brand, currently Dawn) to look like contiki.com/en-ca. Work happens in the theme repo `40Two-ca/tnn-shopifytheme-nationexperiences`; `main` is linked to a demo store, so pushes land there directly.

## Current state
First pass shipped 2026-09-04 on Shopify Horizon 4.1.5: Contiki-style tokens (Archivo 900 headings, Jost body, one accent colour = palette colour 1, pill buttons), trip-card blocks driven by `custom.*` metafields or `badge:` / `duration:` tags, new home sections (trip finder, feature tiles, testimonials, destination tiles, book-with-confidence, partner logos), rebuilt header/footer/home/collection/product templates. Review and merchant to-do list in `docs/contiki-review.md` in the repo. Verified on the demo store: GitHub sync rejects out-of-range JSON template values (validator script in the session scratchpad caught 9); home, collection and product pages render as designed. Two example products created (Toronto trip, Jasper pond hockey); tags drive the badge and meta row, and the `custom.itinerary_days` metafield drives the product-page itinerary timeline.

Nation Gear folded in 2026-09-10: 11 apparel styles from nationgear.ca (type Gear, `gear-` SKUs) with their own `product.gear` / `collection.gear` templates, a Nation Gear collection plus 6 sub-collections, and a Gear main-menu dropdown. Trips are type Experience with `exp-` SKUs; see [[2026-09-10 Gear vs Experience split by product type]].

## Open questions
- FAQ answers covering cancellations and payment terms are drafts written from the live product copy; the Nation Experiences team needs to confirm them before production.
- Expedia Cruises partner link points at the North East Edmonton franchise page (id 200019), confirmed from search results rather than a page load because the site blocks bots. Worth a human click.
- Product pages have a tall empty column under the media when a trip has a single image; worth a look once real photography lands.
- Store still needs: dark wordmark for the white header, hero + tile photos, `main-menu` / `footer` menus, partner logos, and the `custom.*` product metafield definitions.
- Store currency is USD while gear/trip prices are CAD numbers; switch before go-live.
- Accent shipped as volt green (`#D2FF28`); confirm with the team or swap in one setting.

## Links
[[The Nation Network]] · [[40Two]]

## Log
- 2026-09-04 — Reviewed Contiki, rebuilt the theme (3 commits), pushed to main.
- 2026-09-04 — Demo store checked (draft theme preview), sync fixes pushed, Toronto example product added.
- 2026-09-04 — Jasper product added; stock-photo placeholders and richer hero shipped (see "Stock photos" in docs/contiki-review.md).
- 2026-09-04 — Trip finder switched to text boxes; itinerary timeline section added with its metafield defined and filled.
- 2026-09-04 — Trip FAQs, stats and inclusions shipped; page width narrowed to 1440px after a UX review; partner logos linked with UTM tags.
- 2026-09-10 - Imported Nation Gear (11 styles), collections + Gear menu, gear templates pushed and assigned.
