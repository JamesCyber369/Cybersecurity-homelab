# 🍯 Phase 10 — Honeypot Deployment (Cowrie)

**Status:** ✅ Complete

---

## 🎯 Goals

- Deploy a honeypot to capture and analyze attack attempts
- Simulate real attacker behavior in a controlled environment
- Capture credentials, commands, and techniques used by attackers
- Generate threat intelligence data for SIEM analysis
- Practice SOC analyst log review and incident documentation

---

## 🔍 What Is A Honeypot — In Plain Terms

A honeypot is a decoy system designed to attract attackers. It looks like a real, vulnerable target — but everything the attacker does is secretly recorded.

In electrical terms: like installing a fake panel with fake breakers that looks completely real — anyone who tries to tamper with it triggers logging and you can watch exactly what they do, step by step.

---

## 🔄 Tool Selection — Why Cowrie Instead Of T-Pot

The original plan called for T-Pot, a full-featured honeypot platform. T-Pot requires a minimum of 8GB dedicated RAM and 128GB disk — exceeding available resources on the current 16GB lab server.

**Cowrie** was selected instead — a focused, production-grade SSH/Telnet honeypot used by real security researchers and threat intelligence teams. It captures everything an attacker does when they connect: credentials attempted, commands typed, files downloaded, and more.

---

## 🖥️ Deployment Details

| Setting | Value |
|---|---|
| **Deployed On** | ubuntu-server-01 (existing VM) |
| **Cowrie Version** | 3.0.6 |
| **Listen Port** | 2222 (SSH honeypot) |
| **Log Location** | /home/cowrie/cowrie/var/log/cowrie/ |

---

## 🔧 Deployment Process

1. Installed system dependencies (git, python3, virtualenv, libssl-dev, etc.)
2. Created dedicated `cowrie` system user for isolation
3. Cloned Cowrie repository from GitHub
4. Created Python virtual environment
5. Installed Python requirements via pip
6. Installed Cowrie package
7. Started service with `cowrie start`
8. Verified listening on port 2222 via `ss -tlnp`

---

## 🧪 First Attack Simulation

Immediately after deployment, performed a simulated attack from the management laptop to verify Cowrie was capturing correctly:

**Attack method:** SSH connection to port 2222 using default credentials

**What Cowrie captured:**
```
CMD: whoami — Command found: whoami
CMD: ls — Command found: ls
```

Every command typed inside the fake shell was logged automatically — exactly what a real attacker's session would look like.

---

## 🔍 What The Log Data Means For A SOC Analyst

When reviewing Cowrie logs, a SOC analyst looks for:

| Log Entry | What It Tells You |
|---|---|
| Login attempt + password | Credentials attackers commonly try |
| `whoami` command | Attacker checking what user they have |
| `ls`, `cat /etc/passwd` | Attacker doing reconnaissance |
| `wget` or `curl` commands | Attacker trying to download malware |
| `useradd` commands | Attacker trying to create persistence |
| `chmod +x` commands | Attacker trying to make files executable |

---

## 🗺️ MITRE ATT&CK Mapping

| Technique | ID | What Was Simulated |
|---|---|---|
| Brute Force | T1110 | Password attempts on SSH |
| Valid Accounts | T1078 | Using credentials to gain access |
| System Information Discovery | T1082 | Running whoami, checking system |
| File and Directory Discovery | T1083 | Running ls command |

---

## ⚡ Electrical Mapping

| Security Term | Electrical Equivalent |
|---|---|
| Honeypot | Fake panel installed to catch tamperers |
| Cowrie fake shell | Everything looks real but triggers logging |
| Attack logs | The tamper alarm record showing exactly what was touched |
| Credential capture | Recording which "keys" were tried on the fake lock |

---

## 📝 Still To Do

- Forward Cowrie logs to Wazuh SIEM for automated alerting
- Run extended attack simulations using Kali Linux
- Deploy Cowrie to capture real internet-facing attacks (via port forwarding)
- Map captured techniques to full MITRE ATT&CK framework
- Write formal incident reports based on captured data

---

[← Phase 09](../09-vulnerability-scanning/README.md) | [Next: Suricata IDS →](../11-suricata-ids/README.md)
