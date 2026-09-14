---
type: infrastructure
status: active
tags: [40two, cloudways, wordpress]
updated: 2026-09-14
---


# Cloudways Hosting

Client WordPress hosting for [[40Two]]. DigitalOcean Toronto region (Canadian data residency), Cloudflare in front.

## Servers (Sep 2026)
- **40Two-ClientSites-1** and **-2** — shared servers for client WordPress sites, ~$102.50/mo combined
- **Insulation Snakes** — dedicated, ~$216.50/mo, runs [[Insulation Snakes]]' QuotePro Laravel app
- 18 apps total (12 on CS-1, 4 on CS-2, 2 on Insulation Snakes); hosting billed back under QBO "Website Hosting" (33) and "Website Maintenance" (32). Billing status per app: see the "40Two Hosting & Licence Audit" artifact (2026-09-14).

## Pricing
Managed WP hosting + maintenance: published Sep 2026 as Hosting & Maintenance $83/mo or Maintenance Only $63/mo per site (was $50–$85 tiers). Legacy clients still on $17 hosting + $55 maintenance (Canline, Sunset via Head Office Corp, hpcpa.ca) or annual lump sums (Shift $408, Superfly $408, rsbjr $288, Great Circle $876, ServiceMaster golf $250).

## Tooling
- Cloudways MCP server added to Claude Desktop (mcp-remote bridge, X-Access-Token auth) on the Windows PC — appears in Cowork as the `cloudways` local server.
- Maintenance via ManageWP; see [[MainWP Evaluation]].

## Links
[[Claude Integrations]] · [[Disrupt Dial]]

## Log
- 2026-09-07 — Weekly check: all 3 servers healthy (CS-1 disk 65%); 4 apps with critical vulns (WP core RCE 9.1, ManageWP Worker auth bypass 9.8, AIO WP Migration RCE 8.8): OLD-insulationsnakes.com, Cold-fix.com, simplysuperfly.com (CS-2 duplicate), rsbjr.ca. Copilot insights need a subscription.
- 2026-09-14 — Weekly check: all 3 servers healthy (CS-1 disk 65.5%, CPU ≤10%). Same 4 apps still unpatched a week on: OLD-insulationsnakes.com (25 vulns, incl. exploited AIO WP Migration RCE), Cold-fix.com (16), simplysuperfly.com CS-2 duplicate (16), rsbjr.ca (4). Minor: Canlinepipeline.com AIO Unlimited Ext, Shift.Support inactive Health Check, Great Circle Solar inactive AIO Unlimited Ext. Involvi.ca now live on CS-2 (Sep 9). ManageWP "new collaborator added" email Sep 8 — unverified.
- 2026-09-14 — Hosting & licence audit (artifact "40Two Hosting & Licence Audit"): unbilled apps are DDTC (since 2023-06), involvi.ca (since 2026-09-09) and the insulationsnakes.com WP site (only QuotePro $442/mo billed); simplysuperfly.com WP copy on CS-2 is an orphan; Elementor Pro Expert licence also carries 3 TNN sites; ThemePunch, LayerSlider and Motion.page subscriptions are not recovered from any client.
