---
type: reference
status: active
tags: [claude, vault]
updated: 2026-09-03
---


# Vault Conventions for Claude

Rules Claude follows when writing to this vault. Mirrors the `vault` skill.

## Every session that does real work
1. Clone (or pull) the repo.
2. Append to `Daily/YYYY-MM-DD.md` (create from `Templates/Daily.md` if missing) under **Work log**: 2–6 bullets of what was done, with `[[wikilinks]]` to every project/client/infra page touched. Record decisions under **Decisions** and unfinished items under **Open threads**.
3. Update the relevant `Projects/`, `Clients/`, or `Infrastructure/` page: current state, open items, a one-line entry in its **Log**. Bump `updated:`.
4. If a real decision was made, add `Decisions/YYYY-MM-DD Short title.md` from the template and link it from the project page.
5. Commit with a message like `daily: 2026-09-03 — Truck Outfitters kickoff, QBO MCP prod keys` and push. Pull with rebase first; if a conflict hits a daily note, keep both sides.

## Scheduled briefs
The briefs are Cowork scheduled tasks bound to Mike's PC with the vault folder attached — they edit files in place via device_bash and never run git; the Obsidian Git plugin pushes.
Morning brief → fill the **Morning brief** section of today's note. End-of-day brief → fill **End of day**. Weekly health check → append a short summary under **Work log** on Monday.

## Style
- Prose and short bullets; no walls of text. Dates as `YYYY-MM-DD`.
- Frontmatter on every note: `type`, `updated`; projects/clients/infra also `status` and `tags`.
- New pages use the templates; file names are the note titles (Title Case, no dates except daily/decision notes).
- Never store secrets — record where they live.
- Don't duplicate: if a fact belongs on a project page, put it there and link from the daily note.
- Update [[Home]] when a project starts, ends, or changes status.
