# 💿 Phase 03 — OS Installation

**Status:** ✅ Complete

---

## 🎯 Goals

- Install Proxmox VE on the active server
- Configure network settings
- Access the Proxmox web management interface

---

## 📋 Final Configuration

| Setting | Value |
|---|---|
| **OS** | Proxmox VE 9.2.2 |
| **Hostname** | proxmox.local |
| **IP Address** | 10.0.0.50/24 |
| **Gateway** | 10.0.0.1 |
| **DNS** | 10.0.0.1 |
| **Filesystem** | ext4 |
| **Installed Disk** | Samsung 240GB |
| **Timezone** | America/New_York |

---

## 🔍 Real Troubleshooting Log

### Issue 1 — Server Had Prior OPNsense Installation
The server arrived with a fully configured OPNsense firewall installation — complete with production VLANs, DMZ zones, and site-to-site VPN. This was wiped and replaced with Proxmox.

### Issue 2 — BIOS Boot Priority
USB drive was set as 4th boot priority behind the internal hard disk. Fixed by entering BIOS and setting USB as first boot device.

### Issue 3 — USB 3.0 Port Incompatibility
The 2018-era BIOS would not boot from USB 3.0 ports. Resolved by moving the USB drive to a USB 2.0 (black) port instead.

### Issue 4 — NIC Mapping Mismatch
After installation, Proxmox was unreachable because the physical port connected to the switch mapped to nic1, not nic0 as configured. Fixed by editing /etc/network/interfaces and changing bridge-ports from nic0 to nic1, then restarting networking.

---

## 🧠 Key Lesson

Physical port labeling on enterprise hardware does not always match logical interface naming inside the OS. Always verify with ip addr, not by assumption.

---

[← Phase 02](../02-network-setup/README.md) | [Next: Proxmox Configuration →](../04-proxmox-cluster/README.md)
