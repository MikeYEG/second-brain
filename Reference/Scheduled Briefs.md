---
type: reference
status: active
tags: [claude, automation]
updated: 2026-09-24
---


# Scheduled Briefs

Recurring Claude tasks (all times America/Edmonton).

## Morning brief — weekdays 7:00 AM
Sections: projects needing attention · Indeed jobs ([[Job Search]]) · recruiter messages · waiting-on list · repo health · client sites & security · 40Two business pulse · 40Two financial analysis (AR, AP, insights from the QBO MCP, plus last human activity in the QBO audit trail) · government tenders ([[Government Contracts]]) · Vercel deploys · LinkedIn post seed ([[LinkedIn Content]]).
Calendar pulled from Google Calendar and the 40Two Outlook calendar; chat reviewed from Teams and the 40Two Slack.

## End-of-day brief — weekdays ~5:00 PM
What moved since the morning brief, what's still open, tomorrow's shape.

## Weekly web server health check — Mondays 6:00 AM
Read-only checks of Cloudways servers/apps, Vercel projects, Supabase projects, plus a 7-day review of hosting emails from Gmail and the 40Two Outlook mailbox. Digest emailed to mike@infinitysquared.net.

## Monthly Involvi site review: 1st Wednesday 9:00 AM
Fires every Wednesday and exits unless the day is 1 to 7. Re-runs PageSpeed, the SEO crawl, UX spot checks and the Cloudways vuln scan for involvi.ca; writes a dated audit note to `Projects/Involvi Audit Data/`, ticks done items on [[Involvi Website Refresh]], builds that month's client PDF, updates the "Involvi Website Review" deck, drafts (never sends) the email to Ashley in the 40Two Outlook, and adds a send To Do to the Daily note.

## Vault integration
Each brief should write its summary into that day's note in `Daily/` (morning → "Morning brief", EOD → "End of day"). See [[Vault Conventions for Claude]].
