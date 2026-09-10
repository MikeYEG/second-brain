---
type: decision
date: 2026-09-10
project: Nation Experiences Shopify Theme
status: accepted
updated: 2026-09-10
---

# Gear vs Experience split by product type

## Context
Nation Gear apparel now sits in the same Shopify store as the trips. Mike asked for backend separation and suggested `exp-` / `gear-` SKU prefixes to drive collection filtering.

## Decision
Product type (`Experience` / `Gear`) is the separator: smart collections filter on type (plus tags for gear sub-collections), and the buy button says "Book now" only for type Experience. SKUs are still prefixed `exp-` / `gear-` for search, exports and reporting. Gear uses `product.gear` / `collection.gear` templates; `product.json` / `collection.json` stay the trip layouts.

## Alternatives considered
- SKU prefix as the filter: Shopify smart collections cannot filter on SKU.
- Make the retail layout the default template: rejected to leave the existing trip pages untouched; new gear imports need Template = product.gear (bulk editor supports it).

## Consequences
New products must get the right product type; new gear products need the gear template assigned.
