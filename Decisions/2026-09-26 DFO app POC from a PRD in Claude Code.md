---
type: decision
date: 2026-09-26
project: Daily Faceoff App
status: accepted
updated: 2026-09-26
---

# DFO app POC from a PRD in Claude Code

## Context

Concept screens for a Daily Faceoff app were ready. The open question was whether to build a web mockup in chat or a real proof of concept. The risky parts (live DFO data, push alerts, running on phones) can't be proven from a cloud chat session.

## Decision

Write a POC PRD, then build in Claude Code in a new repo, `dailyfaceoff-app`: Expo (React Native) app plus a small Node service that holds the DFO API key, caches data for the app, and polls goalies every 60 s to send pushes. No changes to DFO's backend for the POC.

## Alternatives considered

- Another clickable web mockup in chat: adds little over the canvas and proves none of the risks.
- Webhook from `dailyfaceoff-rails` (`PlayerNews` already triggers revalidation) for instant alerts: faster, but a backend change; deferred to v1.

## Consequences

- Scope is Goalies, Lines and goalie alerts only; Home and News wait for v1.
- The alert service needs an owner and hosting before the live game-night test.
