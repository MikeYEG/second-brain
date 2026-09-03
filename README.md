# Mike's Vault

Central knowledge repository for everything Mike and Claude work on. It is an Obsidian vault backed by a private GitHub repo, so both Mike (via Obsidian + the Git plugin) and Claude (from cloud sessions and scheduled briefs) can read and write it.

Start at [[Home]].

## How it is organised

| Folder | What goes there | Note name |
|---|---|---|
| `Daily/` | One note per day: what moved, decisions, open threads. Claude appends here at the end of every session and from the morning/EOD briefs. | `YYYY-MM-DD` |
| `Projects/` | One page per initiative — status, goals, decisions, links to daily notes. | Project name |
| `Clients/` | One page per client or prospect — contacts, engagements, commercial terms. | Client name |
| `Decisions/` | Short decision records so "why did we do it that way" is answerable later. | `YYYY-MM-DD Short title` |
| `Infrastructure/` | Servers, stacks, hosting, DNS, self-hosted services — what runs where. | Host/stack name |
| `Reference/` | Runbooks, how-tos, snippets, checklists that are reused. | Descriptive title |
| `Templates/` | Obsidian templates for the note types above. | — |
| `Attachments/` | Images, PDFs, exports referenced from notes. | — |

## Conventions

- Every note has YAML frontmatter with at least `type` and `updated`; projects and clients also carry `status` and `tags`.
- Link generously with `[[wikilinks]]` — the graph is only useful if notes are connected. Link daily notes to the projects they touch and vice versa.
- Daily notes are append-only logs. Anything durable (a decision, a credential location, a runbook) gets promoted to the right folder and linked from the daily note.
- Decisions are recorded once, in `Decisions/`, and linked from the project page. Don't rewrite history — add a new decision that supersedes the old one.
- No secrets in the vault. Record *where* a credential lives (Vaultwarden, `.env.<service>` on the droplet), never the value.
- Status values: `active`, `paused`, `done`, `idea`.

## Setup on a new machine

1. Clone this repo.
2. Open the folder in Obsidian ("Open folder as vault").
3. Install the **Git** community plugin (Vinzent03/obsidian-git) and enable auto pull/push (e.g. every 10 minutes, pull on startup). Claude commits from the cloud side, so keeping auto-pull on avoids merge conflicts.
4. Daily notes and Templates core plugins are pre-configured in `.obsidian/`.

## How Claude uses it

Cloud sessions clone the repo, append to today's daily note, update any project/client/decision pages that changed, commit with a descriptive message, and push. Scheduled briefs (morning, end-of-day, weekly server health) write their summaries into the day's note. See `Reference/Vault Conventions for Claude` for the exact rules Claude follows.
