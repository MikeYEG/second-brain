---
type: project
status: active
tags: [tools, price-watch, automation, personal]
updated: 2026-09-12
---


# DeWalt & Husky Deal Watch

Daily price watch on DeWalt 60V FlexVolt batteries and bare tools, and Husky 61"/72" mobile workbenches. Anchored on Home Depot Canada with the store set to Edmonton Windermere (T6W 0L8), with four other retailers swept each run for anything cheaper.

## Current state
- Scheduled task `Daily tool deal watch (DeWalt 60V / Husky bench)` runs 9:00 AM Edmonton daily: re-reads every tracked SKU in a browser, sweeps the other retailers, rewrites the JSON data block in a published Claude artifact, and republishes to the same URL.
- 28 tracked items across three groups — batteries (11), 60V bare tools & attachments (9), Husky benches (8).
- The artifact is the live view; `Projects/Deal Watch Data/` is the durable record. Step 6 of the task writes it on every run (added 2026-09-12).

## Open items
- Both 72" heavy-duty Husky benches (matte black, matte grey) are out of stock online and not sold in-store — watch for a restock or a replacement colour. Only the lighter standard-duty gloss red at $1,198 is orderable.
- Older DCB612 12Ah is out of stock online at Home Depot; the newer DCB6112 has taken its shelf slot at Windermere.
- Nothing has cleared a target since the watch opened except the 61" gloss-white bench at $928 (standard-duty, lighter build than the tracked heavy-duty ones).

## Facts
- Flag rules shown on the page: batteries ≤ $28/Ah (strong buy ≤ $24/Ah); 60V bare tools and attachments ≥ 15% off or any bare-tool clearance; Husky 61" ≤ $999, 72" ≤ $1,399.
- Best battery value on the board is the DCB609-2 9.0Ah 2-pack at $428 — $23.78/Ah, inside the strong-buy line.
- Retailer coverage: Home Depot (anchor, only source for Husky — it's their house brand); KMS Tools (full FlexVolt dealer, Edmonton store, carries bare 60V tools Home Depot doesn't list); Walmart.ca (marketplace listings from real dealers); Amazon.ca (genuine DeWalt listings mixed in among third-party replacement packs); Canadian Tire (no 60V FlexVolt at all, 12V/20V MAX only, no Husky); Rona/Lowe's (no 60V packs or bare tools, no Husky).
- Canadian Tire and Rona stay on the sweep specifically to catch the day they start carrying the line.
- History files: `price-history.csv` is append-only, one row per SKU per day (`date, group, model, sku, retailer, price_cad, ah, packs`); `YYYY-MM-DD.json` is the full data block for that run. Backfilled 2026-09-12 covering 2026-09-08 onward. The artifact caps each item's in-page history at 60 entries, so the CSV outlives it.

## Log
- 2026-09-08: watch opened; baseline pulled from Home Depot with the store set to Edmonton Windermere. Two markdowns on day one — DCB606 at 24% off, 72" Husky bench at 18% off.
- 2026-09-09: widened past Home Depot. DCB612 at $328 from both KMS and Walmart, $91 under Home Depot. DCB609-2 picked up a markdown to $428 ($23.78/Ah).
- 2026-09-10: found the DCS578B bare saw on Amazon at $278, well under Home Depot and KMS. Added DCST972B ($299) and the gloss-white 61" bench at $928 — first bench under the $999 line.
- 2026-09-11: added DCS781X1 miter saw kit ($999, 20% off) and the matte-grey 72" bench after the black went out of stock. 61" matte-black bench restocked at $1,198.
- 2026-09-12: Amazon cut the DCS578B bare saw $278 → $269 (Power Tools Inc, 10 left), the only tracked price that moved. Both 72" heavy-duty benches now out of stock online. Added DCB6112 12Ah ($429, in stock Windermere), DCS781B bare 12" miter saw ($969), and a genuine DCB609 on Amazon ($334). History exported to the vault for the first time and the daily task wired to keep it current.

## Links
[[Claude Integrations]] · [[Scheduled Briefs]]
