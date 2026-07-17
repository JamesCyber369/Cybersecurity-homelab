# 🌐 Phase 02 — Network Setup & IPMI Access

**Status:** ✅ Complete

---

## 🎯 Goals

- Connect server to network via powerline adapters
- Access IPMI interface from laptop
- Identify CPU model via remote console
- Document IP addresses and network layout

---

## 🏗️ Network Architecture

Internet Router (Floor 1)
↓
TP-Link AV1000 Powerline Adapter
↓ (through electrical wiring)
TP-Link AV1000 Powerline Adapter (Floor 2)
↓
8-Port Gigabit Switch
↓
Server (IPMI port) + Laptop

---

## 🛒 Hardware Used

| Item | Status |
|---|---|
| TP-Link AV1000 Powerline Kit | ✅ |
| 8-Port Gigabit Switch | ✅ |
| Cat6 Ethernet Cables | ✅ |
| USB to Ethernet Adapter | ✅ |
| C13 Power Cords | ✅ |

---

## 🔍 Real Troubleshooting Log

### Issue 1 — Identifying The Correct IPMI Port
Supermicro servers do not clearly label the IPMI port on the chassis. Multiple ports were tested before the correct one was identified by cross-referencing the motherboard manual.

### Issue 2 — Cable Stuck In Wrong Port
A cable was mistakenly plugged into a non-standard port and became difficult to remove. Located the release tab and removed without damage.

### Issue 3 — Finding The Server IP With No Documentation
Used Windows Command Prompt ARP scanning to identify the server's IP:
