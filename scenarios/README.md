# 🎯 SOC Analyst Scenarios

This folder documents real-world attack simulations performed in the home lab environment. Each scenario follows a formal incident report structure — the same format used by SOC analysts in real enterprise environments.

---

## 📋 Scenario Index

| # | Scenario | MITRE Technique | Severity | Status |
|---|---|---|---|---|
| [001](./001-ssh-brute-force/) | SSH Brute Force Attack Detection | T1110 — Brute Force | High | ✅ Complete |
| [002](./002-privilege-escalation/) | Privilege Escalation Monitoring | T1548 — Abuse Elevation Control | Medium | ✅ Complete |

---

## 🔍 How These Scenarios Work

Each scenario follows this structure:

1. **Attack simulation** — generate realistic malicious traffic using lab tools
2. **Detection** — verify Wazuh SIEM and/or Suricata IDS captures the activity
3. **Analysis** — determine true positive vs false positive, identify root cause
4. **Response** — document the steps a real SOC analyst would take
5. **MITRE mapping** — map the technique to the ATT&CK framework
6. **Hardening** — recommend specific remediation actions

---

## 🛠️ Lab Environment

| Component | Role |
|---|---|
| vuln-scanner (10.0.0.30) | Attacker machine |
| ubuntu-server-01 (10.0.0.68) | Primary target |
| wazuh-siem (10.0.0.174) | SIEM — detection and alerting |
| k3s-master (10.0.0.66) | Secondary target |
| opnsense-fw | Firewall — network boundary |

---

## 📚 Planned Scenarios

| # | Scenario | MITRE Technique |
|---|---|---|
| 002 | Port Scan Detection | T1046 — Network Service Discovery |
| 003 | Web Application Attack (DVWA) | T1190 — Exploit Public-Facing Application |
| 004 | Lateral Movement Simulation | T1021 — Remote Services |
| 005 | Data Exfiltration Attempt | T1041 — Exfiltration Over C2 Channel |
| 006 | Privilege Escalation | T1068 — Exploitation for Privilege Escalation |
| 007 | Persistence Mechanism | T1053 — Scheduled Task/Job |

---

*All scenarios are conducted in a self-owned, isolated lab environment for educational purposes.*
