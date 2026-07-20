# 🛡️ Phase 11 — IDS/IPS with Suricata

**Status:** ✅ Complete

---

## 🎯 Goals

- Deploy Suricata network intrusion detection system
- Load community detection ruleset
- Monitor live network traffic for threats
- Attempt custom rule creation
- Document findings and lessons learned

---

## 🔍 What Is Suricata — In Plain Terms

Suricata watches all traffic flowing through your network and alerts when it sees something suspicious — a port scan, an exploit attempt, or unusual traffic patterns.

In electrical terms: like a smart circuit monitor that watches current flowing through every wire and triggers an alarm when it detects something that doesn't match normal patterns — a surge, a short, or an unusual draw.

---

## 🖥️ Deployment Details

| Setting | Value |
|---|---|
| **Deployed On** | vuln-scanner VM (existing) |
| **Suricata Version** | 7.0.3 |
| **Interface Monitored** | ens18 |
| **Rules Loaded** | Emerging Threats Community Ruleset |
| **Log Location** | /var/log/suricata/ |

---

## 🔧 Deployment Process

### Installation
```
sudo apt-get install suricata -y
```

### Rules Download
The official `suricata-update` command timed out after an extended period. Resolved by downloading the Emerging Threats ruleset directly:
```
sudo wget https://rules.emergingthreats.net/open/suricata-7.0/emerging.rules.tar.gz
sudo tar -xzvf emerging.rules.tar.gz -C /tmp/
sudo cp /tmp/rules/*.rules /var/lib/suricata/rules/
sudo bash -c 'cat /var/lib/suricata/rules/*.rules > /var/lib/suricata/rules/suricata.rules'
```

### Start Suricata
```
sudo systemctl start suricata
sudo systemctl enable suricata
```

---

## 🔍 Real Troubleshooting Log

### Issue 1 — suricata-update Timed Out
The official update command ran for over an hour without completing.

**Resolution:** Downloaded the Emerging Threats ruleset directly via wget as an alternative method. Successfully loaded 30,000+ community signatures.

### Issue 2 — No Alerts On Standard Nmap Scans
Running standard Nmap scans against lab VMs produced no alerts in fast.log despite Suricata actively processing traffic (confirmed via packet statistics showing 82,000+ packets captured).

**Root cause:** Community rules are primarily tuned for known malware signatures and exploit patterns — not general port scanning activity.

**Lesson:** A quiet SIEM/IDS is not a broken one. In real SOC environments, IDS systems run silently most of the time — alerting only on genuine threats matching known signatures.

### Issue 3 — Custom Rule YAML Config Error
Attempted to create a custom local rule to detect SSH connection attempts. Adding the local.rules file to suricata.yaml introduced a YAML formatting error that prevented Suricata from starting via systemctl.

**Status:** Custom rule not successfully loaded due to YAML indentation conflict. Suricata continues to run using community rules only.

**Lesson:** Suricata's YAML configuration is strict about indentation and formatting. Custom rule files need to follow exact YAML structure. This exercise will be revisited using Wazuh's GUI-based rule editor, which is more forgiving and more representative of how SOC analysts actually create custom detections in enterprise environments.

---

## ✅ What Was Verified Working

- Suricata installed and running on ens18
- 30,000+ Emerging Threats community signatures loaded
- Live packet capture confirmed — 82,233 packets processed, 0 drops during testing
- Log files created and accessible at /var/log/suricata/
- Traffic monitoring active

---

## 🧠 Key Lessons

1. **A quiet IDS is not a broken IDS.** No alerts during normal traffic is expected and correct behavior — the system is working, threats just haven't appeared yet.
2. **YAML configuration files are strict about formatting.** A single indentation error can prevent an entire service from starting — this is why GUI-based tools exist for rule management in enterprise environments.
3. **Community rulesets cover known threats, not all traffic.** Standard port scans don't trigger alerts because they're not in themselves malicious — only scans matching specific known exploit patterns do.

---

## ⚡ Electrical Mapping

| Security Term | Electrical Equivalent |
|---|---|
| Suricata | Smart panel monitor watching every circuit for abnormal current |
| Detection rule | A specific fault signature — "alert if current exceeds X on circuit Y" |
| Fast.log | The fault log — only records when something abnormal is detected |
| Community ruleset | A library of known fault signatures from across the industry |

---

## 📝 Still To Do

- Resolve YAML config issue and load custom local.rules successfully
- Connect Suricata alerts to Wazuh SIEM for unified monitoring
- Test detection of known exploit traffic patterns
- Write custom detection rules through Wazuh (more practical approach)

---

[← Phase 10](../10-honeypot/README.md) | [Next: Terraform/Ansible →](../12-terraform-ansible/README.md)
