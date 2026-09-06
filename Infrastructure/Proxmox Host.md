---
type: infrastructure
status: active
tags: [home, proxmox, virtualization]
updated: 2026-09-06
---

# Proxmox Host

Home Proxmox VE 9.1 host, node `pve` — a separate physical box from the [[Frigate NVR Box]].

## Hardware
- i7-6700 (8 threads), 64 GB RAM, legacy-BIOS boot
- Storage: `local`, `local-lvm`, `wd-drive`; ZFS available

## Guests
- 100 ma-hermes · 101 ma-openclaw · 102 Win11 · 103 UnifiOS
- [[Home Assistant]] — HAOS VM (from 2026-09-06)

## Backups
- Planned 2026-09-06: NFS storage `synology` on the Synology NAS, daily 03:00 job for all VMs, retention 7/4/3 — checklist on [[Home Assistant]].

## Access
- Web UI on port 8006 as root@pam; credentials in Vaultwarden

## Log
- 2026-09-06 — Page created while planning the [[Home Assistant]] rebuild; no VM backup job existed yet.
