# 🔥 Phase 05 — Firewall Deployment (OPNsense)

**Status:** 🔄 In Progress

---

## 🎯 Goals

- Deploy a virtualized firewall as a VM on Proxmox
- Configure WAN and LAN interfaces
- Set up network segmentation
- Verify internet connectivity through the firewall

---

## 🔄 Why OPNsense Instead of pfSense

The original plan called for pfSense. Netgate restructured their distribution to require account creation and a $0.00 store checkout — switched to OPNsense which offers a direct ISO download with no account required. This server had also previously run a real OPNsense production configuration (discovered during Phase 03), making it a natural fit.

---

## 🖥️ VM Specifications

| Setting | Value |
|---|---|
| **Name** | opnsense-fw |
| **OS** | OPNsense 26.1.6 |
| **CPU** | 1 core |
| **RAM** | 3072 MiB |
| **Disk** | 10GB |
| **WAN Interface** | em0 — bridge vmbr0 — 10.0.0.87 |
| **LAN Interface** | vtnet0 — bridge vmbr1 — 192.168.1.1 |

---

## 🔍 Real Troubleshooting Log

### Issue 1 — Compressed ISO Format
Downloaded file was .iso.bz2. Extracted directly on the Proxmox host using bunzip2 before use.

### Issue 2 — Installer RAM Requirement
OPNsense installer required minimum 3GB RAM. Initial VM had 1GB allocated. Increased to 3072 MiB and restarted.

### Issue 3 — Interface Assignment Loop
Auto-detection looped with a single NIC. Added additional virtual NICs and manually specified interface names.

### Issue 4 — WAN/LAN Bridge Swap
Both interfaces ended up on wrong networks. Traced in Proxmox Hardware tab and corrected bridge assignments — WAN to vmbr0, LAN to vmbr1.

### Issue 5 — ICMP Blocked By Default
100% ping loss made it appear OPNsense had no internet. Root cause was OPNsense blocking ICMP by default. Confirmed real connectivity via fetch http://google.com which succeeded.

### Issue 6 — Physical Port Identification
Used dmesg -w (live kernel log monitoring) to identify correct physical port for nic2 while plugging cables — definitive method that avoids all guessing.

### Issue 7 — DNS Resolution Not Working From LAN Clients
OPNsense can resolve DNS for itself. LAN clients cannot get DNS responses despite correct configuration. Under active investigation — likely a stale reply-to binding from the WAN/LAN swap.

### Issue 8 — NAT Outbound Rules Not Generating For LAN
Automatic NAT rules only covered loopback network, not 192.168.1.0/24. Manual hybrid NAT rule added but not yet fully resolving internet access for LAN clients.

---

## 🧠 Key Lessons

- ping is not a reliable connectivity test through a firewall
- dmesg -w is the definitive way to identify physical network ports
- OPNsense manages its config through config.xml — manual file edits to other locations are silently ignored
- TCP success does not imply UDP success — test both independently

---

## 📝 Still To Do

- Resolve DNS and NAT issues for LAN clients
- Configure VLANs for network segmentation
- Define firewall rules between segments

---

[← Phase 04](../04-proxmox-cluster/README.md) | [Next: Wazuh SIEM →](../06-wazuh-siem/README.md)
