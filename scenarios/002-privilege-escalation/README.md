# Incident Report #002 — Privilege Escalation Monitoring

**Date:** July 25, 2026
**Analyst:** James Sinclair
**Severity:** Low-Medium (Level 3)
**Status:** Closed — Authorized Activity Confirmed

---

## 📋 Incident Summary

Wazuh SIEM detected repeated privilege escalation activity on ubuntu-server-01 — specifically, multiple successful sudo to ROOT executions paired with rapid login/logout session cycling within a short timeframe. While this activity was authorized (analyst performing lab maintenance), this pattern would trigger investigation in a real SOC environment as it matches common post-exploitation behavior.

---

## 🔍 Detection Details

| Field | Value |
|---|---|
| **Alert Time** | Jul 25, 2026 @ 20:39 — 20:45 |
| **Rule IDs** | 5402, 5501, 5502 |
| **Agent** | ubuntu-server-01 (10.0.0.68) |
| **Total Events** | 340 hits over 24 hours |
| **Key Pattern** | Repeated sudo ROOT + login/logout cycling |
| **Detection Tool** | Wazuh SIEM — Threat Hunting |

### Alert Breakdown

| Rule ID | Description | Level | Count |
|---|---|---|---|
| 5402 | Successful sudo to ROOT executed | 3 | Multiple |
| 5501 | PAM: Login session opened | 3 | Multiple |
| 5502 | PAM: Login session closed | 3 | Multiple |

---

## 🗺️ MITRE ATT&CK Mapping

| Field | Detail |
|---|---|
| **Tactic** | Privilege Escalation (TA0004) |
| **Technique** | Abuse Elevation Control Mechanism (T1548) |
| **Sub-technique** | Sudo and Sudo Caching (T1548.003) |
| **Description** | Adversaries may perform sudo caching and/or use the sudoers file to elevate privileges |

---

## 📖 Investigation Narrative

### What Was Observed
Wazuh's Threat Hunting module showed 340 security events from ubuntu-server-01 over a 24-hour period. The most frequent pattern involved Rule 5402 (sudo to ROOT) consistently paired with Rules 5501 and 5502 (login session open/close) in rapid succession — multiple times within minutes of each other.

### Why This Pattern Is Suspicious In A Real Environment
In a real SOC investigation, this combination of events would raise several questions:

1. **Who is executing sudo commands?** — Is this an authorized admin or a compromised account?
2. **Why are sessions opening and closing so rapidly?** — Could indicate automated scripts or an attacker covering tracks
3. **What commands are being run as root?** — The log shows the elevation but not the specific command executed
4. **Is this expected activity for this server?** — A production web server repeatedly elevating to root would be unusual

### Investigation Steps Taken
1. Identified the pattern in Wazuh Threat Hunting
2. Noted the timing — all events clustered around lab maintenance window
3. Cross-referenced with known authorized activity (analyst performing lab work)
4. Confirmed this is authorized activity — no escalation required

---

## ✅ Disposition

**Authorized Activity** — The sudo commands and session cycling were performed by the lab analyst during legitimate system maintenance including:
- UFW firewall configuration
- Wazuh agent management
- Log file review

**No further action required.**

---

## 🧠 What A Real SOC Analyst Would Do Differently

In a real enterprise environment, this investigation would include:

| Step | Action |
|---|---|
| 1 | Check which specific user account executed the sudo commands |
| 2 | Review `/var/log/auth.log` for the exact commands run as root |
| 3 | Verify the activity against a change management ticket or maintenance window |
| 4 | Check if the source IP of the sessions matches expected admin workstations |
| 5 | Review any files created or modified during the elevated sessions |
| 6 | If unauthorized — immediately revoke sudo access and isolate the system |

---

## 🔧 Detection Rule Context

Wazuh's built-in rules automatically detected this activity without any custom configuration:

- **Rule 5402** — fires on any successful sudo to root
- **Rule 5501/5502** — fires on every PAM login/logout session

These are low-level (Level 3) rules by default because sudo usage is common in Linux administration. In a production environment, a SOC team would raise the alert level for servers where root access should be rare, or create custom rules that alert on sudo usage outside of approved maintenance windows.

---

## 💡 Key Takeaway — The Value Of Baseline Behavior

This scenario demonstrates one of the most important SOC analyst skills: **establishing and recognizing normal behavior**. The same sudo events that are completely expected on a lab server would be highly suspicious on a production database server that should never require direct admin access. 

Context is everything — a good SOC analyst knows what "normal" looks like for each system they monitor.

---

## 🔒 Hardening Recommendations

| Recommendation | Priority |
|---|---|
| Enable detailed sudo logging (log specific commands, not just elevation) | High |
| Configure sudoers to restrict which commands each user can run as root | High |
| Set up alerting for sudo usage outside of approved maintenance windows | Medium |
| Implement privileged access management (PAM) solution for root access | Medium |
| Review and minimize accounts with sudo privileges | High |

---

## 📁 Evidence

- Wazuh Threat Hunting screenshot showing 340 events and rule descriptions
- Event data from ubuntu-server-01 agent, July 25 2026

---

*This incident was investigated as part of a self-managed cybersecurity home lab project. All systems involved are owned and operated by the analyst.*

---

[← Back to Scenarios](../README.md)
