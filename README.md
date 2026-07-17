# 🖥️ From Electrician to IT: Building a Cybersecurity Home Lab from Scratch

> **A real-world journey of career transition from Electrical Work into IT & Cybersecurity — documented from day one.**

[![Status](https://img.shields.io/badge/Status-Active-brightgreen)]()
[![Phase](https://img.shields.io/badge/Current%20Phase-Kubernetes%20Complete-blue)]()
[![Goal](https://img.shields.io/badge/Goal-Cloud%20%26%20AI%20Security-purple)]()

---

## 👤 About Me

I am transitioning from a career in **electrical work** into **IT and Cybersecurity**, with a focus on **Cloud Security** and **AI Security**. Rather than just studying theory, I chose to get hands-on — acquiring real enterprise server hardware and building a functional home lab completely from scratch.

This repository documents every step of that journey — from receiving unknown hardware with no documentation, physically inspecting and identifying every component, sourcing missing parts, setting up networking, installing a hypervisor, and ultimately building a full enterprise-grade security lab.

> Coming from electrical work gave me a strong foundation in physical infrastructure, systems thinking, and troubleshooting — skills that translate directly into IT.

---

## 🎯 Project Goals

- Build a fully functional enterprise home lab using virtualization
- Learn hardware identification, inspection, and documentation
- Configure server networking and remote management via IPMI
- Deploy and manage operating systems on bare metal
- Build cloud infrastructure skills using Proxmox
- Practice cybersecurity with SIEM, IDS/IPS, and vulnerability scanning
- Develop AI/LLM security skills on real deployed models
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
| [07](./07-kubernetes/) | Kubernetes Cluster | ✅ Complete |
| [08](./08-openstack-cloud/) | Private Cloud — OpenStack | 📋 Planned |
| [09](./09-vulnerability-scanning/) | Vulnerability Scanning | 📋 Planned |
| [10](./10-honeypot/) | Honeypot Deployment | 📋 Planned |
| [11](./11-suricata-ids/) | IDS/IPS — Suricata | 📋 Planned |
| [12](./12-terraform-ansible/) | Infrastructure as Code | 📋 Planned |
| [13](./13-ai-llm-security/) | AI/LLM Security Lab | 📋 Planned |
| [14](./14-mlsecops-pipeline/) | MLSecOps Pipeline | 📋 Planned |

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

## 🔄 The Electrical → IT Connection

| Electrical Concept | IT Equivalent |
|---|---|
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

---

*"The best way to learn is to build."* ⚡
