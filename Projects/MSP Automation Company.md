---
type: project
status: active
tags: [msp, automation, n8n]
updated: 2026-09-21
---


# MSP Automation Company

A new MSP aiming for ~95% self-serviced and ~99% automated operations, with standardized fixes applied uniformly across all customers.

## Shape
- Target customers: 1–100 seat businesses
- Scope: endpoints, Microsoft 365, backup/DR, network gear
- Launch team: Mike + 1–2 techs
- Tooling: NinjaOne (RMM + Tickets), n8n as a Rewst alternative; open to other suggestions

## Approach
- Build an n8n-based Rewst.io alternative, self-hosted in Azure — internal-first, open-source later once proven.
- Decided to write a full operating/architecture blueprint before scaffolding code or workflows.

## Current state
- Target go-live: 2026-10-15, defined as ready to take a paying customer end to end (pilot-grade), not the finished 95% self-service vision.
- Stack: NinjaOne for RMM, ticketing and all backup (M365, desktop, server); Huntress for EDR; Invoice Ninja for billing. n8n stays off the critical path until launch.
- NinjaOne account meeting booked for the week of 2026-09-21.
- Go-live plan lives in a Claude Doc (timeline, workstreams, open decisions, risks): [Autonomic MSP: Go-Live Plan](https://claude.ai/code/artifact/a0b12560-410b-4d92-8f2b-3c048e342b5d)
- Client portal PRD (v0.3, build gated behind the NinjaOne forms experiment; tabs: PRD, Technical design, Build plan for Claude Code): [Autonomic MSP: Client Portal PRD](https://claude.ai/code/artifact/dee4d10d-3e19-4e08-b1aa-22ac09ec0954)
- Weekly review: scheduled task "Weekly MSP go-live review", Mondays 7:30 AM MT, bound to the PC with this vault attached; it logs into the plan doc and here.

## Decisions
- [[2026-09-19 NinjaOne for RMM tickets and backup with Huntress EDR]]

## Open items
- Legal and brand home: inside 40Two or a new entity
- Pilot environment: own fleet, 40Two, or a friendly small business
- Huntress ITDR in the standard plan or not
- Microsoft licensing path: reseller via distributor, or customers keep existing licensing at launch
- Documentation and credential vault: NinjaOne Documentation or Hudu
- CIPP timing; network standard (UniFi or Meraki) deferred until the first network customer
- MSA, insurance quote, per-seat pricing once vendor quotes are in

## Links
- [[MSP Selection - Vancouver Client]] (adjacent market research)
- Blueprint artifacts: [The Autonomic MSP](https://claude.ai/artifact/UnEsLnhemhu1VdBwC5nRKG), [The n8n MSP Stack](https://claude.ai/artifact/6poppnfEAgv6b8QSoWZmNR)
- RIPP (the n8n control-plane product) is a separate track; the MSP does not depend on it for launch.

## Log
- 2026-09-19: Moved from idea to active. Go-live set for 2026-10-15, stack confirmed (NinjaOne + Huntress), go-live plan doc written, weekly Monday review scheduled.
- 2026-09-19: Weekly review (baseline): On track. NinjaOne overview call booked Mon 2026-09-21; Huntress account, insurance quote and MSA not started; no decision overdue.
- 2026-09-21: Weekly review: On track. 0 of 29 ticked, no movement since baseline; NinjaOne overview call today 14:00 MT; Huntress, insurance and MSA not started; three decisions due 2026-09-25; no MSP blocks on the calendar.
- 2026-09-21: Client portal spec v0.1 drafted. CIPP fork rejected; custom thin portal (Next.js, Entra ID, Postgres RLS, n8n executor) planned for after go-live. Nine open questions listed in the spec.
- 2026-09-21: Portal spec expanded to a full PRD v0.2 for Claude Code: requirement IDs with acceptance tests, extensibility model, scaling path, milestones M0 to M7. Multi-MSP schema now in scope; real-vendor work (M6) held until after go-live.
- 2026-09-21: PRD v0.2 critical review done (tab in the PRD doc). Not ready to build; recommended path is NinjaOne end-user forms plus n8n for 60 to 90 days, then revisit. GDAP or CSP is not required for M365 automation (admin consent or CIPP direct tenant works); five critical security findings recorded if the portal is ever built.
- 2026-09-21: Portal PRD v0.3: review fixes applied with staged scope. Build gate and kill criteria added; revisit build vs buy 2027-01-15. Still open for Mike: real cost quotes, insurer confirmation, legal check, NinjaOne webhook and rate-limit facts, patch cover when away.
