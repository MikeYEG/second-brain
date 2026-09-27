---
type: project
status: active
tags: [tnn, dailyfaceoff, mobile, expo]
updated: 2026-09-26
---

# Daily Faceoff App

## Goal

Phone app for DFO's game-day tools (Starting Goalies, Line Combos) with push alerts when a followed goalie is confirmed. POC first: prove it runs on DFO's existing data with no backend changes.

## Current state

- Site analysis done; concept screens (Home, Goalies, Lines, Article, Alerts) designed and polished on the "DFO App Concepts" canvas.
- POC PRD written (living doc in Claude Docs; copy at `docs/PRD.md` in the repo).
- Repo `dailyfaceoff-app` created at `E:\Github Repos\dailyfaceoff-app` (pnpm workspace: `apps/mobile`, `apps/alerts`, `packages/shared`, `docs/`). One local commit; no remote yet.
- Next: Milestone 1 (data foundation) in Claude Code using the kickoff prompt at the end of the PRD.
- Post-POC roadmap researched (see Links): Phase 1 webhook goalie alerts, manual My Team, line-change alerts, goalie outlook; league sync and comments gated on third parties.

## Decisions

- [[2026-09-26 DFO app POC from a PRD in Claude Code]]

## Open questions

- Separate DFO API key for the app, or reuse the website's?
- 5v5 Hockey API terms for app use (source of the DFO Rating).
- Headshot rights; team logos vs colour chips.
- Apple/Google developer accounts under TNN; who owns the alert service in production.
- GitHub remote: `nationnetwork` org (like next-dailyfaceoff) or personal first?

## Links

- Design canvas: https://claude.ai/artifact/P2fFFNxsY4bUyGeWuecQM2
- PRD (living): https://claude.ai/code/artifact/562da2f4-f82e-4e1e-8af7-6e2a0dde1ec4
- Roadmap and competitors: https://claude.ai/code/artifact/660c8861-3e63-4bfc-b6ed-694ff6293b2d
- Repo: 40Two-ca/dailyfaceoff-app
- Reference repos: `next-dailyfaceoff`, `dailyfaceoff-rails`
- Client: [[The Nation Network]]

## Log

- 2026-09-26: Analyzed dailyfaceoff.com; designed and polished app concepts; wrote POC PRD; created `dailyfaceoff-app` repo. Found in the Rails API: past goalie slates match news by the player's current team (wrong team after trades), stats are current-season only, and the site's 0-100 rating comes from the 5v5 API `overall_score`, not `goalie_rating`.
- 2026-09-26: Researched post-POC roadmap: LWL and Dobber Goalie Post are the only hockey goalie apps; Yahoo API now read-only with approval; Disqus native SDK and SSO are Business-only; Google Play bans gambling ads alongside odds or performance tracking in non-gambling apps.
