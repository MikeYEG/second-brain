---
type: decision
date: 2026-09-18
project: "[[Truck Outfitters Shopify Migration]]"
status: accepted
updated: 2026-09-18
---

# Sync alerts name the exact fix

## Context
The nightly Slack message was counts and a log path: "5 attribute conflicts · 4 unmatched" on a night that changed nothing, posted as an ALERT. The reader is [[Truck Outfitters]] staff in Slack — no access to `C:\AIMS-Sync\logs`, no knowledge of the sync's vocabulary — so nothing in it could be acted on. A first redesign (explanations + SKU lists + generic advice) was rejected: it still didn't say exactly what to change.

## Decision
- Every counter above zero gets its own section: what it means, the items behind it, and a `→` line saying what to change. Names are the customer's — the column by its AIMS header from `export-format.json` (never the sync's role name), the export file name, the family's `Product Desc`.
- An attribute conflict names the rows to fix: when one value is on ≥ 3 rows in 4, the others are listed with their vehicles as the rows to correct; with no dominant value it says the part may genuinely differ by vehicle — a store-rules change (`listMetafields`), not an AIMS one.
- A fix needing a command on the server is addressed "for whoever looks after the sync", with `--store <key>` filled in, so the message can be forwarded as is.
- **`unmatched` no longer raises an alert.** It is discontinued-list SKUs in no catalog and not on Shopify — nearly always nothing to fix, and named every night. Still printed, with the one check worth doing (the part on sale under a differently typed SKU).
- All wording lives in one file, `Notify/IssueGuide.cs`; each remedy is a claim about sync behaviour and must stay true to the runbook.

## Alternatives considered
- Explanations only, no item lists (rejected — still sends the reader to a log they can't open).
- New-vs-ongoing diffing against the previous night (deferred — bigger change; demoting `unmatched` removed the worst nightly repeat).
- A configurable per-store support contact instead of "whoever looks after the sync" (rejected for now — config key, wizard field and docs for one sentence).
- Tagging `run_events` with a kind and reading it back (rejected — schema change plus parsing log prose; issues are held in memory for the run instead, `sync.db` unchanged).

## Consequences
- Eagle's first night on the new kit will likely arrive as OK rather than ALERT — a change of alert rule, not evidence anything was fixed. The attribute conflicts still alert until corrected in AIMS.
- No fingerprints move; nothing re-writes.
- Lists are capped (5 alerting / 3 outstanding / 10 names per line); over 12,000 characters the message keeps headings and arrows and drops items rather than be cut or refused by Slack.
- Standing bar for anything customer-facing in the tool (dashboard next): name the SKU, file, AIMS column, values and the change.
- Shipped in commit `3f90fa1`; kit `2026.09.18-06`.
