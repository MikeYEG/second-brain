---
type: project
status: active
tags: [personal, data, facebook, vercel]
updated: 2026-09-08
---

# Waffle House Board

## Goal
Track the Western Waffle House Facebook giveaway group (private, ~35.6K members): every winning spot posted since June 1, the boards still standing (price, holders, winners, comments), hot/cold numbers, money in and out, the house's margin, and Mike's and Greg Weir's own entries. Free/cheap by design — no database, everything is one JSON record in a private repo.

## Current state
- Repo `MikeYEG/waffle-house-board` (local `E:\Github Repos\waffle-house-board`), Vercel project `waffle-house-board` auto-deploys `web/` from main; the same page is the claude.ai artifact "Waffle House Board".
- The record is `data/wwh.json` (meta, retail price table, raw post texts + comments, derived draws/boards/nights/players, my_entries). `scraper/wwh.py` does `ingest → rebuild → build`; `scraper/browser_scraper.js` is pasted into the Facebook tab via Claude in Chrome (feed scrape → IndexedDB → export, plus per-post comment capture).
- Daily Claude task "Daily Waffle House draw review" (6:30 AM, bound to the PC) re-scrapes and rebuilds; Windows Task Scheduler "WWH autopush" (7:15) commits and pushes (`scripts/autopush.ps1`).
- App tabs: Hot & Cold (window, mains/minis, sleeping, vs expected, fairness tests), Draw ledger, Money, Players (leaderboard, popular picks, claims from comments, player cards), House (revenue, prize cost, margin, weekly trend, draw clock), Mike's spots / Greg's spots (entry log + EV calculator).
- Valuation: cash prizes as stated; item prizes by the house ratio (median cash prize ÷ pot = 0.758) unless a retail price is on file; labelled stated / retail / implied / credit / similar / estimated.
- Fairness so far: winning positions consistent with a fair draw (chi-square p≈0.74); heavy buyers win roughly in proportion to spots held.

## Decisions
- 2026-09-06 — Value item prizes "by what the house is telling us" (pot × cash ratio) rather than guessing retail; retail table overrides when known.
- 2026-09-07 — No Supabase/DB sync; keep the project free (static Vercel + JSON in git).

## Open questions
- Board posts are deleted ~2 weeks after they fill, so spend history before Aug 23 only exists for wins named in the nightly posts; Mike and Greg log older entries by hand (Greg's Aug 8 Blackstone win: 2 spots bought, only #39 visible).
- Comment capture needs Chrome to paint a frame between scroll nudges (background tab) — the daily task alternates `__nudge()` with tiny screenshots; Chrome also blocks repeat automatic downloads from facebook.com, so the export may need "allow automatic downloads" for the site.
- Fold the comment pass and retail lookups into the daily task prompt (needs delete/recreate + Mike's approval in the desktop app).

## Links
- Artifact: claude.ai "Waffle House Board" · Vercel: waffle-house-board.vercel.app
- [[Claude Integrations]] (scheduled task, Chrome extension) · [[Vercel and Supabase]]

## Log
- 2026-09-05 — Built the record, scraper and app; GitHub + Vercel; weekly → daily task; autopush job.
- 2026-09-06 — House-math valuation, Players dropdowns + custom ranges, Mike's/Greg's tabs, House tab, review of what to add next.
- 2026-09-07 — Comment capture (claims, house random assignments, Random Verified draw timestamps) for 14 boards; retail price table; fairness tests; EV calculator; what's-new feed; weekly trends; draw clock; claims panel; parser test suite (15 tests, real-post fixtures); ingest --dry-run; fixed "Phillips 5500" cash false positive and claim ranges ("24,49" is two spots, "25-26" a range).
- 2026-09-08 — Daily run (581 draws, 9 retail prices added). Then fixed Tonight-tab staleness: group search filters on creation date and under-returns, so 14 of 16 open boards were 2 days old. Posts now record their permalink; `browser_refresh.js` (permalink subset of the scraper) + `wwh.py stale` re-read a board directly; `captured_at`, `signal` (last admin OPEN/FULL comment) and `open_called`/`open_est` (free spots already called in the comments); Tonight tab shows read-age per board, a freshness filter and struck-through called spots. New "WWH afternoon refresh" task at 2:15 PM MT. Tests 15 → 26.
