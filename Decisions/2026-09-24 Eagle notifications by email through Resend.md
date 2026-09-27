---
type: decision
date: 2026-09-24
project: "[[Truck Outfitters Shopify Migration]]"
status: accepted
updated: 2026-09-24
---

# Eagle notifications by email through Resend

## Context
Eagle wants the nightly sync and image-fetch messages by email instead of Teams; Slack stays for 40Two's monitoring. 40two.ca mail is Microsoft 365 (SPF `-all`, DMARC quarantine). Mike did not want an email API key on the customer's server that could send as 40two.ca.

## Decision
- Email is a third channel beside Slack and Teams, sent through Resend's HTTPS API (spec R41, `docs/superpowers/specs/2026-09-24-email-notifications-design.md` in the AIMStoShopify repo).
- One sending-only Resend key per store (`RESEND_API_KEY_<STORE>` in `.secrets\shopify.env`), limited to a sending subdomain (placeholder `notify.40two.ca`): a leaked key cannot pass as anyone @40two.ca, and revoking it touches no other store.
- Sender `TTO Shopify Eagle Sync <TTO-Shopify-EagleSync@notify.40two.ca>`, Reply-To Mike; recipients live in the server's `config.json`, so whoever runs the server can change them.
- Subject `<yyyy-MM-dd>-AIMS-Eagle-ShopifySync` / `-ImageSync`; the run's log is attached instead of named; every run.

## Alternatives considered
- Hashing or encrypting the key - impossible or pointless: Resend needs the key itself, and the server would hold whatever decrypts it.
- Azure Logic App relay sending from an M365 shared mailbox - no key on the server, but one more service to look after.
- M365 SMTP relay trusted by Eagle's IP - no secret, but needs a static IP and port 25, and trusts everything behind that IP.
- Resend behind a hosted relay; Microsoft Graph with a certificate; SMTP AUTH with a password - more moving parts, or a credential that can send as 40Two to anyone.

## Consequences
- The server already holds a permanent Shopify token, so the key does not raise the bar for protecting `.secrets\`; its blast radius is bounded by the subdomain.
- 40Two does a one-time Resend setup and adds DNS records (runbook: `docs/operations.md` section 2).
- Nothing emails until a store has an `email` block and its key; installing the kit changes nothing by itself.
