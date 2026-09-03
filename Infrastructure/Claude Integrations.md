---
type: infrastructure
status: active
tags: [claude, mcp]
updated: 2026-09-03
---


# Claude Integrations

What Claude can reach, and how.

## Connectors (Claude account)
Gmail (mike@infinitysquared.net), Google Calendar, Google Drive, Microsoft 365 (40Two tenant — Outlook, Teams, SharePoint), Slack (40Two workspace), Supabase, Vercel, Indeed, QuickBooks via the custom "40Two Claude MCP QBO" connector.

Note: the Better Collective Google Workspace account can't be connected — that domain is managed by their own Claude Enterprise org.

## Self-hosted MCP servers
- QBO MCP — qbo.mcp.40two.ca on the [[40Two Droplet]]
- Cloudways MCP — local server on the Windows PC (see [[Cloudways Hosting]])
- Planned: Postgres MCP on the [[TNN Analytics Droplet]]; MainWP MCP ([[MainWP Evaluation]])

## Scheduled tasks
See [[Scheduled Briefs]].

## This vault
Private GitHub repo `MikeYEG/second-brain`; local copy on the Windows PC synced by the Obsidian Git plugin. Cowork sessions and the scheduled briefs (morning, end-of-day, weekly server check — all bound to the PC with this folder attached) write straight into the local vault and the Git plugin pushes; Code-tab cloud sessions with the repo attached push directly. Rules in [[Vault Conventions for Claude]] and the `vault` skill.
