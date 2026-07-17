# 📊 Phase 06 — SIEM Deployment with Wazuh

**Status:** ✅ Complete

---

## 🎯 Goals

- Deploy Wazuh SIEM as a virtual machine on Proxmox
- Access the Wazuh web dashboard
- Install a Wazuh agent on Ubuntu VM
- Verify Ubuntu appears as a monitored endpoint
- Begin collecting real security events

---

## 🔍 What Is A SIEM — In Plain Terms

A SIEM is like a security camera system for your entire network. Instead of cameras watching physical spaces, it watches every device — collecting logs, detecting suspicious activity, and alerting when something needs attention.

In electrical terms: like a panel monitoring system that tracks every circuit's activity in real time and alerts you when something draws too much current or trips unexpectedly.

---

## 🖥️ Wazuh Server Specifications

| Setting | Value |
|---|---|
| **Deployment Method** | OVA pre-built virtual appliance |
| **Version** | Wazuh 4.14.6 |
| **VM Name** | wazuh-siem |
| **RAM** | 4GB |
| **CPU** | 2 cores |
| **Network** | vmbr0 |
| **IP Address** | 10.0.0.174 |
| **Dashboard** | https://10.0.0.174 |

---

## 🖥️ Wazuh Agent — Ubuntu VM

| Setting | Value |
|---|---|
| **Agent Name** | ubuntu-server-01 |
| **OS** | Ubuntu 24.04.4 LTS |
| **Wazuh Manager** | 10.0.0.174 |
| **Status** | Active |

---

## 🔧 Deployment Process

1. Downloaded Wazuh OVA directly to Proxmox host using wget
2. Extracted OVA contents using tar to get the .vmdk disk file
3. Created new VM in Proxmox with no disk attached
4. Imported .vmdk disk using qm importdisk
5. Attached disk and set boot order
6. Started VM — booted into pre-installed Wazuh system
7. Confirmed dashboard accessible at https://10.0.0.174
8. Used Wazuh dashboard's built-in agent deployment wizard
9. Installed agent on Ubuntu and configured manager IP
10. Confirmed ubuntu-server-01 appears as active agent

---

## 🔍 Real Troubleshooting Log

### Issue 1 — Full Wazuh Stack Accidentally Installed On Ubuntu
Ran the full Wazuh install script on Ubuntu instead of just the agent. Left behind a conflicting wazuh-manager package blocking the agent install.

**Resolution:** Used sudo apt-get remove --purge wazuh-manager then proceeded with agent-only installation.

### Issue 2 — Manager IP Not Set After Agent Install
The sed command to replace MANAGER_IP placeholder did not execute correctly.

**Resolution:** Manually edited /var/ossec/etc/ossec.conf using nano, replacing MANAGER_IP with 10.0.0.174 directly.

---

## 🧠 Key Lessons

1. Use the application's own deployment wizard when available — generates correct, version-matched commands automatically
2. OVA files are pre-built virtual machines — extract, import as disk, attach to VM, done
3. Installing the wrong component creates harder cleanup problems than not installing anything

---

## ✅ Verified Working

- Wazuh dashboard accessible at https://10.0.0.174
- ubuntu-server-01 appearing as active agent
- Security events and system inventory flowing from Ubuntu to Wazuh

---

[← Phase 05](../05-pfsense-firewall/README.md) | [Next: Kubernetes →](../07-kubernetes/README.md)
