---
type: decision
date: 2026-09-19
project: "[[MSP Automation Company]]"
status: accepted
updated: 2026-09-19
---

# NinjaOne for RMM tickets and backup with Huntress EDR

## Context
The August blueprint left backup open (Ninja Backup vs Cove) and named no EDR vendor. Go-live is set for 2026-10-15, so the launch stack needed to close.

## Decision
- NinjaOne for RMM, ticketing and all backup: M365 (SaaS Backup), desktop and server.
- Huntress for EDR, deployed through NinjaOne as a scheduled automation.

## Alternatives considered
- Cove for backup: strong M365 coverage, but a second console and data model.

## Consequences
- One vendor carries monitoring, tickets and backup, which keeps the automation surface in one API.
- NinjaOne SaaS Backup is a separate SKU from device backup; confirm it is on the quote.
- Still open: Huntress ITDR in the standard plan, documentation vault, CIPP timing.
