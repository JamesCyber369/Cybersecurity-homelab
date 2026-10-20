# 🖥️ Cybersecurity GRC Meets Systems Engineering | Enterprise Home Lab

> **Building real infrastructure to connect security governance, technical implementation, and operational risk.**

[![Status](https://img.shields.io/badge/Status-Active-brightgreen)]()
[![Phase](https://img.shields.io/badge/Current%20Phase-Suricata%20IDS%20Complete-blue)]()
[![Goal](https://img.shields.io/badge/Goal-GRC%20%2B%20Systems%20Engineering-purple)]()

---

## 👤 About Me

I'm a **Cybersecurity Governance, Risk, and Compliance (GRC) professional** with experience in NIST RMF, security control assessments, and federal security compliance. I'm expanding my hands-on understanding of systems engineering so I can better evaluate how security controls work in practice — including the infrastructure dependencies, technical constraints, and operational tradeoffs engineers encounter.

This repository documents my enterprise-style home lab, built from physical Supermicro servers through virtualization, network security, centralized monitoring, identity management, and attack simulations. My goal isn't simply to check whether a control exists; it's to understand **how to implement, validate, troubleshoot, and improve that control without losing sight of system availability and mission needs**.

**Follow the journey as I bridge GRC and systems engineering — from server to user, and from network boundaries to security monitoring.**

---

## 🎯 Project Goals

- Build a fully functional enterprise home lab using virtualization
- Learn hardware identification, inspection, and documentation
- Configure server networking and remote management via IPMI
- Deploy and manage operating systems on bare metal
- Develop systems engineering and hybrid infrastructure fundamentals using Proxmox, Windows Server, and Linux
- Practice cybersecurity with SIEM, IDS/IPS, and vulnerability scanning
- Connect NIST RMF and security control objectives to practical engineering constraints and evidence
- Document everything as a professional portfolio — including real troubleshooting, not just a finished result

---

## 🗺️ Project Phases

| Phase | Project | Status |
|---|---|---|
| [01](./01-hardware-identification/) | Hardware Identification & Inspection | ✅ Complete |
| [02](./02-network-setup/) | Network Setup & IPMI Access | ✅ Complete |
| [03](./03-os-installation/) | OS Installation — Proxmox VE | ✅ Complete |
| [04](./04-proxmox-cluster/) | Proxmox Configuration & First VM | ✅ Complete |
| [05](./05-pfsense-firewall/) | Firewall Deployment — OPNsense | 🔄 In Progress |
| [06](./06-wazuh-siem/) | SIEM Deployment — Wazuh | ✅ Complete |
| [07](./07-kubernetes/) | Kubernetes Cluster — K3s | ✅ Complete |
| [08](./08-openstack-cloud/) | Private Cloud — OpenStack | ⏭️ Skipped |
| [09](./09-vulnerability-scanning/) | Vulnerability Scanning — Nmap | ✅ Complete |
| [10](./10-honeypot/) | Honeypot Deployment — Cowrie | ✅ Complete |
| [11](./11-suricata-ids/) | IDS/IPS — Suricata | ✅ Complete |
| [12](./12-terraform-ansible/) | Infrastructure as Code | 📋 Planned |
| [13](./13-ai-llm-security/) | AI/LLM Security Lab | 📋 Planned |
| [14](./14-mlsecops-pipeline/) | MLSecOps Pipeline | 📋 Planned |

---

## 🧩 Additional Implemented Skills

These completed exercises extend the original numbered phases:

| Area | Documented Work | Status |
|---|---|---|
| [Windows Server & Active Directory](./additional-skills/windows-server-active-directory/) | Windows Server 2022 domain controller, AD DS, domain users, OUs, security groups, and DNS | ✅ Complete |
| [OPNsense WireGuard VPN](./additional-skills/opnsense-wireguard-vpn/) | VPN instance, Windows client, split tunneling, and routing troubleshooting | ✅ Complete |
| [Wireshark & Packet Capture](./additional-skills/wireshark-packet-capture/) | tcpdump/tshark capture, SCP transfer, protocol filtering, and traffic analysis | ✅ Complete |

**Group Policy:** An area of continued development; the Active Directory documentation establishes the domain and accounts, but does not yet document a completed GPO deployment.

## 🎯 Security Detection & Response Scenarios

| Scenario | Technique | Status |
|---|---|---|
| [SSH Brute Force Detection](./scenarios/001-ssh-brute-force/) | MITRE ATT&CK T1110 | ✅ Complete |
| [Privilege Escalation Monitoring](./scenarios/002-privilege-escalation/) | MITRE ATT&CK T1548 | ✅ Complete |

See the [scenario index](./scenarios/) for detection, analysis, response, and hardening notes.

---

## 🖥️ Lab Hardware

### Current Active Setup

| Device | Model | Role | RAM | Status |
|---|---|---|---|---|
| **Active Server** | Supermicro X10SLH-N6-ST031 | Primary Lab Server — Proxmox Host | 16GB DDR3 | ✅ Active |
| Reserved Server 1 | Supermicro SSG-6028R | Reserved for future expansion | 32GB DDR3 | ⏸️ Offline |
| Reserved Server 2 | Supermicro SYS-6018R-WTRT | Reserved for future expansion | 64GB DDR4 | ⏸️ Offline |

### Active Server Specs

| Component | Detail |
|---|---|
| **CPU** | Intel Xeon E3-1231 v3 @ 3.40GHz, 4 cores |
| **RAM** | 16GB DDR3 ECC |
| **OS** | Proxmox VE 9.2.2 |
| **Management IP** | 10.0.0.50 (Proxmox) / 10.0.0.243 (IPMI) |

---

## 🔐 Why This Matters for GRC & Security Engineering

| Engineering Area | Security and Risk Connection |
|---|---|
| Active Directory, users, and groups | Least privilege, access governance, and account management |
| Domain controllers and DNS | Identity dependencies, secure configuration, and service availability |
| OPNsense, network segmentation, and WireGuard | Boundary protection, remote access, and traffic-flow constraints |
| Proxmox VMs and Linux/Windows servers | Configuration baselines, patching, and infrastructure hardening |
| Wazuh, Suricata, and packet analysis | Continuous monitoring, event detection, and validating safeguards |
| Attack simulations and remediation | Control effectiveness, incident analysis, and evidence-driven risk decisions |

---|---|
| Circuit breakers | Firewalls |
| Cable runs & conduit | Network infrastructure |
| Power distribution panels | Server power management |
| Troubleshooting faults | Diagnosing hardware/software issues |
| Reading electrical schematics | Reading network diagrams |
| Safety lockout/tagout protocols | Security access controls |

---

## 📝 Update Log

| Date | Update |
|---|---|
| 2026-05-31 | Project started — hardware received |
| 2026-05-31 | All 3 servers physically inspected and identified |
| 2026-05-31 | All 3 servers confirmed working via power-on test |
| 2026-06-10 | Network setup — powerline adapters and switch configured |
| 2026-06-10 | IPMI access achieved on active server |
| 2026-06-21 | Proxmox VE 9.2.2 installed — Phase 03 complete |
| 2026-06-21 | First VM deployed — Ubuntu Server 24.04.4 LTS — Phase 04 complete |
| 2026-06-23 | OPNsense firewall VM deployed — WAN internet confirmed |
| 2026-06-27 | Network segmentation implemented — internal bridge created |
| 2026-07-01 | Wazuh SIEM deployed — Ubuntu agent connected — Phase 06 complete |
| 2026-07-17 | K3s Kubernetes cluster deployed — Phase 07 complete |
| 2026-07-17 | Nmap network scan — 24 hosts discovered — Phase 09 complete |
| 2026-07-17 | Cowrie SSH honeypot deployed and tested — Phase 10 complete |
| 2026-07-18 | Suricata IDS deployed with Emerging Threats ruleset — Phase 11 complete |
| TBD | OPNsense NAT/routing issue resolved — Phase 05 complete |
| TBD | Infrastructure as Code — Terraform/Ansible |

---

*"To assess a control well, understand the system it protects."*
