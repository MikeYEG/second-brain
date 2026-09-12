---
type: reference
tags: [price-watch, data]
updated: 2026-09-12
---


# Deal Watch Data

Durable history for [[DeWalt & Husky Deal Watch]]. The published artifact caps each item's in-page history at 60 entries and is otherwise the only copy — these files are the record that outlives it.

- `price-history.csv` — append-only. One row per SKU per day: `date, group, model, sku, retailer, price_cad, ah, packs`. Sorted by date, then group, model, retailer, so each run appends a clean block of lines and diffs readably in git.
- `YYYY-MM-DD.json` — the full data block published that day: prices, was-prices, stock lines, retailer coverage notes, and the run log.

Prices are CAD and exclude tax. A missing row for a SKU on a given date means it had no price that day (out of stock or unavailable in the area), not that it was unchanged.
