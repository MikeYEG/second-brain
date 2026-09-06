---
type: decision
date: 2026-09-06
project: Home Assistant
status: accepted
updated: 2026-09-06
---

# 2026-09-06 Home Assistant as HAOS VM on Proxmox

## Context
The laptop running Home Assistant (HAOS with add-ons) died. Daily full backups exist in Google Drive. Options were a Home Assistant Container on the [[Frigate NVR Box]], a HAOS VM on the [[Proxmox Host]], or new dedicated hardware.

## Decision
Run Home Assistant OS as a VM on the existing [[Proxmox Host]] and restore the 2026-09-05 backup in full.

## Alternatives considered
- **Container on the Frigate box** — simplest Docker setup, but no add-ons (Mosquitto, Google Drive Backup, etc. would each need their own container), and HA would share fate with the camera box.
- **New hardware (HA Green / mini PC)** — one-click restore too, but costs money and adds a device; only worth it for isolation, which the Proxmox box already provides.

## Consequences
- Add-ons, Zigbee network and credentials come back from the backup unchanged; Zigbee stick passed through by USB ID.
- Two backup layers from now on: HA → Google Drive (as before) and Proxmox VM → Synology NFS.
- Frigate and anything else that pointed at the laptop's IP need updating (or the VM inherits the old DHCP reservation).
