# 🔬 Wireshark & Packet Capture

**Status:** ✅ Complete
**Category:** Gap-Closing Skill

---

## 🎯 Goals

- Install and use tcpdump for command-line packet capture
- Transfer capture files using SCP
- Analyze captured traffic using Wireshark GUI
- Apply display filters to isolate specific traffic types
- Practice realistic network analyst workflow

---

## 🔧 Tools Used

| Tool | Purpose |
|---|---|
| **tcpdump** | Command-line packet capture on Linux |
| **tshark** | Command-line packet analysis |
| **Wireshark** | GUI-based packet analysis on Windows laptop |
| **SCP** | Secure file transfer from lab VM to laptop |

---

## 🔧 Workflow

1. Captured live traffic on vuln-scanner using tcpdump
2. Generated real lab traffic — Nmap scans, ping, normal network activity
3. Transferred .pcap file from vuln-scanner to laptop via SCP
4. Opened capture in Wireshark GUI for visual analysis
5. Applied display filters to isolate specific protocols

---

## 📊 Protocols Captured

| Protocol | Description |
|---|---|
| ARP | Address resolution — devices mapping IPs to MAC addresses |
| ICMP/ICMPv6 | Ping traffic and network control messages |
| UDP | Connectionless traffic including SSDP and MDNS |
| TCP (SYN) | Nmap port scan connection attempts |

---

## 🔍 Wireshark Filters Used

| Filter | What It Shows |
|---|---|
| `arp` | Address resolution traffic |
| `icmp` | Ping/ICMP packets |
| `tcp.flags.syn == 1` | TCP SYN packets (port scans) |
| `ip.dst == 10.0.0.68` | All traffic destined for Ubuntu |

---

## 🧠 Key Lessons

1. **Capture location matters** — tcpdump only captures traffic that passes through its interface. Traffic between two other devices won't appear unless it passes through the capturing host.
2. **SCP is the standard way** to move capture files from a headless server to a workstation for GUI analysis — this is the realistic enterprise workflow.
3. **ARP traffic reveals device inventory** — every device on a network generates ARP packets, making it useful for passive network discovery.
4. **Display filters vs capture filters** — Wireshark display filters filter what you see after capture; capture filters filter what gets captured. Both are important skills.

---

## ⚡ Electrical Mapping

| Network Term | Electrical Equivalent |
|---|---|
| Packet capture | Clamp meter reading current on a live wire |
| Protocol filter | Isolating one specific circuit from a panel |
| ARP traffic | Devices announcing themselves like breakers labeled on a panel |
| .pcap file | A recorded oscilloscope trace you can review later |

---

[← Back to Additional Skills](../README.md)
