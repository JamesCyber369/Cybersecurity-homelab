# Incident Report #001 — SSH Brute Force Attack Detection

**Date:** July 25, 2026
**Analyst:** James Sinclair
**Severity:** High (Level 10)
**Status:** Closed — Simulated Exercise

---

## 📋 Incident Summary

A brute force authentication attack was detected against the Ubuntu server (10.0.0.68) in the lab environment. Multiple failed SSH login attempts from a single source IP triggered a Wazuh SIEM alert mapped to MITRE ATT&CK technique T1110 (Brute Force).

---

## 🔍 Detection Details

| Field | Value |
|---|---|
| **Alert Time** | Jul 25, 2026 @ 19:58:01 |
| **Rule ID** | 2502 |
| **Rule Description** | syslog: User missed the password more than one time |
| **Severity Level** | 10 — High |
| **Source IP** | 10.0.0.30 (vuln-scanner VM) |
| **Target** | 10.0.0.68 (ubuntu-server-01) |
| **Target Port** | 22 (SSH) |
| **MITRE Technique** | T1110 — Brute Force |
| **MITRE Tactic** | Credential Access |
| **Detection Tool** | Wazuh SIEM |

---

## 🗺️ MITRE ATT&CK Mapping

| Field | Detail |
|---|---|
| **Tactic** | Credential Access (TA0006) |
| **Technique** | Brute Force (T1110) |
| **Sub-technique** | Password Guessing (T1110.001) |
| **Description** | Adversaries may use brute force techniques to gain access to accounts when passwords are unknown or when password hashes are obtained |

---

## 📖 Attack Narrative

1. **Reconnaissance** — Attacker (vuln-scanner, 10.0.0.30) identified an SSH service running on port 22 of the target (ubuntu-server-01, 10.0.0.68) via prior Nmap scan
2. **Initial Access Attempt** — Attacker repeatedly attempted SSH login using invalid username (`wronguser`) and incorrect passwords
3. **Detection** — Wazuh SIEM Rule 2502 triggered after multiple consecutive authentication failures from the same source IP
4. **Alert Generated** — High severity alert (Level 10) created with full MITRE ATT&CK context

---

## 🔬 Analysis

### Is This A True Positive Or False Positive?
**True Positive** — for simulation purposes. The attack traffic was intentionally generated from the vuln-scanner VM to test detection capabilities. In a real environment, traffic of this pattern from an unknown or unexpected source would be treated as a genuine brute force attempt requiring immediate response.

### Why This Attack Is Significant
SSH brute force is one of the most common attack vectors against Linux servers exposed to a network. Attackers use automated tools to attempt thousands of username/password combinations. A successful brute force attack grants full command-line access to the target system.

---

## 🛡️ Response Steps (Simulated)

| Step | Action | Status |
|---|---|---|
| 1 | Alert identified in Wazuh dashboard | ✅ Complete |
| 2 | Source IP identified (10.0.0.30) | ✅ Complete |
| 3 | Confirmed attack pattern — multiple failures same source | ✅ Complete |
| 4 | In real environment: block source IP at firewall | 📋 Simulated |
| 5 | In real environment: notify system owner | 📋 Simulated |
| 6 | In real environment: review auth logs for successful logins | 📋 Simulated |
| 7 | In real environment: reset any potentially compromised credentials | 📋 Simulated |
| 8 | Document and close incident | ✅ Complete |

---

## 🔧 Detection Rule Details

This alert was detected by Wazuh's built-in Rule 2502, which fires when a user fails authentication multiple times. Additionally, a custom rule (100001) was created during this exercise to supplement detection:

```xml
<rule id="100001" level="10">
  <if_matched_sid>5760</if_matched_sid>
  <same_source_ip />
  <description>SSH brute force attack detected from same source IP</description>
  <group>authentication_failures,</group>
</rule>
```

---

## 🧠 Lessons Learned

1. **Wazuh successfully detected the brute force attempt** — confirming the SIEM is correctly ingesting and analyzing SSH authentication logs from the monitored endpoint
2. **MITRE ATT&CK mapping was automatic** — Wazuh mapped the alert to T1110 without manual configuration, which is how enterprise SIEMs are expected to work
3. **SSH on default port 22 is a high-value target** — in a hardened production environment, SSH should either be on a non-standard port, restricted by IP allowlist, or replaced with key-based authentication only (no password auth)

---

## 🔒 Recommended Hardening Actions

| Action | Priority |
|---|---|
| Disable password-based SSH authentication — use key pairs only | High |
| Restrict SSH access by source IP using firewall rules | High |
| Implement fail2ban to automatically block repeated failures | Medium |
| Move SSH to a non-standard port | Low |
| Enable SSH login alerting for all successful logins | Medium |

---

## 📁 Evidence

- Wazuh alert screenshot: `wazuh-t1110-brute-force-alert.png`
- Custom rule file: `local_rules.xml` (Wazuh Server Management → Rules)
- Attack simulation tool: Nmap + manual SSH attempts from vuln-scanner (10.0.0.30)

---

*This incident was a simulated exercise conducted as part of a self-managed cybersecurity home lab project. All systems involved are owned and operated by the analyst. No unauthorized access was attempted.*

---

[← Back to Scenarios](../README.md)
