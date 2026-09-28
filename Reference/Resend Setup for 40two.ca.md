---
type: reference
status: active
tags: [40two, email, resend, aims-sync]
updated: 2026-09-27
---

# Resend Setup for 40two.ca

One-time setup so the AIMS sync can email a store's list through Resend ([[2026-09-24 Eagle notifications by email through Resend]], [[Truck Outfitters Shopify Migration]]). Nothing about 40two.ca's own M365 email changes.

## Facts checked 2026-09-27
- 40two.ca DNS is on **Cloudflare** (`thomas` / `val.ns.cloudflare.com`).
- `notify.40two.ca` had no records - free to use as the sending subdomain.
- Root DMARC `v=DMARC1; p=quarantine; fo=1` has no `sp=`, so it covers the subdomain; Resend's DKIM passes it. Don't add `_dmarc.notify`.

## Steps
1. **Account** - sign up at resend.com with a 40Two admin/shared mailbox; turn on 2FA. Free plan covers a few emails a night (check limits).
2. **Domain** - Domains > Add Domain > `notify.40two.ca`, region North America (us-east-1). Copy the exact records Resend lists; they look like:
   - MX `send.notify` -> `feedback-smtp.us-east-1.amazonses.com`, priority 10
   - TXT `send.notify` -> `v=spf1 include:amazonses.com ~all`
   - TXT `resend._domainkey.notify` -> the domain's own DKIM key (`p=...`)
   - Skip Resend's suggested DMARC record.
3. **Cloudflare** - 40two.ca > DNS > Records > Add record, one per row; Name is only the part shown (Cloudflare appends `.40two.ca`); TTL Auto. Leave the root MX/SPF/DMARC alone. Resend's automatic Cloudflare setup is fine if offered - check all three records after.
4. **Verify** - Resend > the domain > Verify DNS Records. Check by hand: `Resolve-DnsName resend._domainkey.notify.40two.ca -Type TXT`, `Resolve-DnsName send.notify.40two.ca -Type MX`, `... -Type TXT`. Open and click tracking **off**.
5. **Key** - API Keys > Create: name `aims-sync-eagle`, **Sending access**, domain **`notify.40two.ca`** (not all domains). If Resend won't limit a sending key to one domain, stop - the security case depends on it. The key (`re_...`) shows once: store it in Vaultwarden as "Resend - aims-sync-eagle", nowhere else.
6. **Server** (after kit `2026.09.25-01` is installed), from `C:\AIMS-Sync`: `AimsSync-2026.09.25-01.exe setup notify --store eagle` - Enter through Slack/Teams, yes to email: key, Eagle's recipients, sender `TTO Shopify Eagle Sync <TTO-Shopify-EagleSync@notify.40two.ca>`, reply-to Mike, name `Eagle`, level every run. Then `... setup notify --store eagle --test`; Resend's Emails page shows delivery. Ask Eagle to safe-sender the address.

## If the key is misused
Delete it in Resend (nothing else uses it), create a new one the same way, enter it with `setup notify --store eagle` (yes to replacing the key).

## Where else
The AIMStoShopify repo's `docs/operations.md` section 2, "Email through Resend: one-time setup".
