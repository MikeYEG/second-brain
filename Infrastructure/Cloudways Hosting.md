---
type: infrastructure
status: active
tags: [40two, cloudways, wordpress]
updated: 2026-09-07
---


# Cloudways Hosting

Client WordPress hosting for [[40Two]]. DigitalOcean Toronto region (Canadian data residency), Cloudflare in front.

## Servers (Sep 2026)
- **40Two-ClientSites-1** and **-2** — shared servers for client WordPress sites, ~$102.50/mo combined
- **Insulation Snakes** — dedicated, ~$216.50/mo, runs [[Insulation Snakes]]' QuotePro Laravel app
- 17 apps total; hosting billed back at ~$442/mo total under QBO "Website Hosting"

## Pricing
Managed WP hosting + maintenance: $50–$85 CAD/site/month.

## Tooling
- Cloudways MCP server added to Claude Desktop (mcp-remote bridge, X-Access-Token auth) on the Windows PC — appears in Cowork as the `cloudways` local server.
- Maintenance via ManageWP; see [[MainWP Evaluation]].

## Links
[[Claude Integrations]] · [[Disrupt Dial]]

## Log
- 2026-09-07 — Weekly check: all 3 servers healthy (CS-1 disk 65%); 4 apps with critical vulns (WP core RCE 9.1, ManageWP Worker auth bypass 9.8, AIO WP Migration RCE 8.8): OLD-insulationsnakes.com, Cold-fix.com, simplysuperfly.com (CS-2 duplicate), rsbjr.ca. Copilot insights need a subscription.
