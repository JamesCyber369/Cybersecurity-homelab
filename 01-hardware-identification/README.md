# 📦 Phase 01 — Hardware Identification & Inspection

**Status:** ✅ Complete
**Date:** May 2026

---

## 🎯 The Challenge

Received 3 enterprise rackmount servers with no documentation, no OS installed, and no power cords. Goal was to identify every component through physical inspection before spending any money.

---

## 🔍 Inspection Methodology

1. Physical exterior inspection
2. Open chassis and photograph interior
3. Motherboard identification via PCB labels
4. PSU identification via unit label
5. RAM identification — physically removed and read sticks
6. CPU socket inspection
7. Expansion card identification
8. Cable inspection and verification
9. Power on test

---

## 🖥️ Device 1 — Supermicro SSG-6028R

| Component | Spec |
|---|---|
| **System** | Supermicro SSG-6028R |
| **Form Factor** | 2U Rackmount |
| **Motherboard** | Supermicro X9DRH-7TF |
| **CPU Socket** | Dual LGA2011 |
| **CPU 1** | Intel Xeon E5-2600 v1/v2 |
| **CPU 2** | Empty |
| **RAM** | 2× Kingston 16GB DDR3-1600 ECC = 32GB |
| **PSU** | Supermicro PWS-920P-SQ 920W |
| **NIC** | Mellanox ConnectX-3 EN 10GbE |
| **Drive Bays** | 12× 3.5" Hot-Swap |

---

## 🖥️ Device 2 — Supermicro SYS-6018R-WTRT

| Component | Spec |
|---|---|
| **System** | Supermicro SYS-6018R-WTRT |
| **Form Factor** | 1U Rackmount |
| **Motherboard** | Supermicro X10DRW-iT |
| **CPU Socket** | Dual LGA2011-v3 |
| **RAM** | 4× Kingston 16GB DDR4-2133 ECC = 64GB |
| **NIC** | Intel 82599ES Dual Port 10G SFP+ |
| **Drive Bays** | 4× Hot-Swap |

---

## 🖥️ Device 3 — Supermicro X10SLHN (Active Lab Server)

| Component | Spec |
|---|---|
| **Form Factor** | 1U Rackmount |
| **Motherboard** | Supermicro X10SLHN Rev 4.711 |
| **CPU** | Intel Xeon E3-1231 v3 @ 3.40GHz |
| **CPU Socket** | Single LGA1150 |
| **RAM** | 2× Crucial 8GB DDR3-1600 ECC = 16GB |
| **PSU** | Supermicro PWS-341P-1H 341W |
| **Drive Bays** | 4× Hot-Swap |

---

## ⚡ Power On Test Results

| Device | Powers On | Fans | LEDs | Beep |
|---|---|---|---|---|
| Device 1 | ✅ | ✅ | ✅ | ⚠️ Normal POST beep |
| Device 2 | ✅ | ✅ | ✅ | ⚠️ Normal POST beep |
| Device 3 | ✅ | ✅ | ✅ | ✅ Silent |

---

[← Back to Main](../README.md) | [Next: Network Setup →](../02-network-setup/README.md)
