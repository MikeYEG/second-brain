---
type: decision
status: accepted
date: 2026-09-03
project: "[[Claude Integrations]]"
updated: 2026-09-03
---


# Obsidian vault on private GitHub for shared knowledge

## Context
Mike wanted a central, Obsidian-like knowledge repository of what he and Claude work on. Claude's built-in memory is fact-oriented and not browsable; a connected local folder only works while the PC is online.

## Decision
An Obsidian vault backed by a private GitHub repo. Claude clones/pushes from cloud sessions and scheduled briefs; Mike syncs locally with the Obsidian Git plugin.

## Alternatives considered
- Local folder connected to Cowork — simplest but unavailable to scheduled tasks.
- Self-hosted Gitea — same workflow, more to run.
- Google Drive / SharePoint — no linking, poor Obsidian fit.

## Consequences
Git history for free; conflict risk if both sides edit the same daily note without pulling — auto-pull on the Obsidian side mitigates it.
