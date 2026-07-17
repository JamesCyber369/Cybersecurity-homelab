# 🏗️ Phase 04 — Proxmox Configuration & First VM

**Status:** ✅ Complete

---

## 🎯 Goals

- Configure Proxmox storage for VM management
- Deploy first virtual machine
- Install Ubuntu Server as guest OS
- Verify full network connectivity for the VM

---

## 🖥️ First VM — Specifications

| Setting | Value |
|---|---|
| **Name** | ubuntu-server-01 |
| **OS** | Ubuntu Server 24.04.4 LTS |
| **CPU** | 1 socket / 2 cores |
| **RAM** | 2048 MiB |
| **Disk** | 20GB local-lvm |
| **Network** | vmbr0 |
| **IP Address** | 10.0.0.x (DHCP) |
| **SSH** | Enabled |

---

## 🔍 Real Troubleshooting Log

### Issue 1 — Wrong ISO Download Link
First attempt to download Ubuntu ISO using Proxmox's Download from URL tool failed — copied a redirect tracking page instead of the direct ISO link. Resolved by navigating to releases.ubuntu.com directly and copying the raw file link.

### Issue 2 — CD-ROM Unmount Failure On Reboot
After installation, the VM tried to boot back into the installer instead of the installed OS. Resolved by stopping the VM, editing Hardware settings to set CD/DVD Drive to "Do not use any media," then restarting.

---

## 🧠 Key Lesson

Virtual CD/DVD drives need to be explicitly detached after an OS install — unlike physical hardware where you remove a USB drive manually.

---

## Verification

Confirmed full network connectivity with 0% packet loss from laptop to VM.

---

[← Phase 03](../03-os-installation/README.md) | [Next: Firewall →](../05-pfsense-firewall/README.md)
