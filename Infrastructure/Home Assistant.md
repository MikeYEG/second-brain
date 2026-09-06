---
type: infrastructure
status: active
tags: [home, homeassistant, proxmox, zigbee, backups]
updated: 2026-09-06
---

# Home Assistant

Home automation — Home Assistant OS as a VM on the [[Proxmox Host]] (from 2026-09-06; previously a physical laptop that died).

## What it is
- HAOS VM (helper script `haos-vm.sh` from community-scripts, 2 cores / 4 GB / 32 GB, q35, UEFI)
- Zigbee USB coordinator passed through to the VM by USB vendor/device ID (ZHA)
- Add-ons restored from backup: Mosquitto (MQTT broker used by the [[Frigate NVR Box]]), Google Drive Backup, others per `backup.json`

## Access
- Web UI on port 8123 on the VM's IP; user credentials in Vaultwarden
- Google Drive: folder `Home Assistant Backups` in Mike's infinitysquared Drive — daily full backups from the Google Drive Backup add-on

## Backups
- **HA layer** — Google Drive Backup add-on, daily; keep as-is (offsite, restores anywhere). Optional second location: HA network storage → Synology SMB share.
- **VM layer** — Proxmox backup job → Synology NFS share `proxmox-backups` (storage ID `synology`), daily 03:00, snapshot mode, ZSTD, retention keep-last 7 / weekly 4 / monthly 3.

## Open items (week of 2026-09-07)
- [ ] Create HAOS VM on the [[Proxmox Host]] via the helper script (Advanced → storage on the SSD-backed pool)
- [ ] Plug Zigbee stick into the Proxmox host (USB 2.0 port, short extension) → VM Hardware → Add USB by vendor/device ID → power-cycle VM
- [ ] Restore `Full Backup 2026-09-05 17:46:37.tar` via onboarding "Restore from backup", all boxes ticked (fallback: the 09-04 backup)
- [ ] Verify ZHA; fix serial port under ZHA → Configure if needed (never re-pair / migrate radio)
- [ ] Old-IP references: give the VM the laptop's DHCP reservation, or update Frigate `mqtt: host:` and anything else that pointed at the laptop
- [ ] Synology: shared folder `proxmox-backups`, enable NFS, NFS rule for the Proxmox IP (RW, map root to admin)
- [ ] Proxmox: Datacenter → Storage → Add NFS `synology` (content VZDump), retention 7/4/3
- [ ] Proxmox: Datacenter → Backup → daily 03:00 job, all VMs, snapshot, ZSTD, email on failure → Run now
- [ ] Check VM Options → QEMU Guest Agent enabled
- [ ] Test restore of the first backup to a spare VM ID, then delete it
- [ ] Confirm the Google Drive Backup add-on is running and still uploading after the restore
- [ ] Update this page + [[Frigate NVR Box]] with the final IP/MQTT host

## Maintenance
- HA updates from Settings → System → Updates; take a Proxmox snapshot of the VM before major upgrades
- Watch the Google Drive folder size (daily ~600 MB, add-on prunes by its own retention)

## Log
- 2026-09-06 — Laptop died. Backups confirmed in Google Drive. Decided on a HAOS VM on Proxmox (see [[2026-09-06 Home Assistant as HAOS VM on Proxmox]]); runbook and backup plan written, work scheduled for this week.
