# 🖥️ Windows Server 2022 & Active Directory

**Status:** ✅ Complete
**Category:** Gap-Closing Skill

---

## 🎯 Goals

- Deploy Windows Server 2022 as a VM in Proxmox
- Install and configure Active Directory Domain Services
- Promote server to a domain controller
- Create Organizational Units, users, and security groups
- Practice core sysadmin workflows used in MSP and enterprise environments

---

## 🔧 VM Specifications

| Setting | Value |
|---|---|
| **VM Name** | windows-server-01 |
| **OS** | Windows Server 2022 Standard (Desktop Experience) |
| **CPU** | 2 cores |
| **RAM** | 4096 MiB |
| **Disk** | 50GB |
| **Network** | vmbr0 |
| **BIOS** | OVMF (UEFI) |
| **Machine Type** | q35 |

---

## 🏗️ Active Directory Configuration

| Setting | Value |
|---|---|
| **Domain Name** | lab.local |
| **NetBIOS Name** | LAB |
| **Forest Level** | Windows Server 2016 |
| **Domain Level** | Windows Server 2016 |
| **DNS** | Installed on domain controller |

---

## 🔧 Deployment Process

1. Downloaded Windows Server 2022 Evaluation ISO (180-day free trial)
2. Uploaded ISO to Proxmox local storage
3. Created VM with UEFI/OVMF BIOS and TPM 2.0 (required for Windows Server 2022)
4. Completed Windows Server installation with Desktop Experience for full GUI
5. Set Administrator password
6. Installed Active Directory Domain Services role via Server Manager
7. Promoted server to domain controller and created new forest lab.local
8. Server rebooted and came up as a domain controller
9. Logged in as LAB\Administrator confirming domain authentication working

---

## 🏛️ Active Directory Structure Created

lab.local (Domain)

└── IT Department (Organizational Unit)

    ├── jsmith (Domain User)

    └── IT-Admins (Security Group)

        └── jsmith (Member)

---

## 🔧 Tasks Completed

| Task | Tool Used |
|---|---|
| Install AD DS role | Server Manager |
| Promote to domain controller | AD DS Configuration Wizard |
| Create Organizational Unit | Active Directory Users and Computers |
| Create domain user account | Active Directory Users and Computers |
| Create security group | Active Directory Users and Computers |
| Assign user to group | Active Directory Users and Computers |

---

## 🧠 Key Concepts

| Term | Plain Definition |
|---|---|
| **Active Directory** | Microsoft's directory service — central database of all users, computers, and resources |
| **Domain Controller** | The server that runs Active Directory and authenticates all logins |
| **Domain** | A logical grouping of network objects managed by one AD instance |
| **OU** | A folder in AD used to organize users and computers by department |
| **Security Group** | A collection of users that share the same permissions |
| **GPO** | Rules applied automatically to users or computers in AD |

---

## ⚡ Electrical Mapping

| AD Term | Electrical Equivalent |
|---|---|
| Active Directory | The master panel schedule listing every circuit and who has access |
| Domain Controller | The main breaker panel — controls and authenticates everything downstream |
| Organizational Unit | A labeled circuit group such as 2nd Floor Outlets |
| Security Group | A shared breaker feeding multiple outlets — one switch controls all |
| Domain User | A keyed lock — only authorized users can access specific circuits |

---

## 📝 Why This Matters For Target Roles

Active Directory is the backbone of nearly every Windows-based enterprise environment. MSPs like Acumen Technology manage AD for their clients daily. SOC analysts monitor its logs to detect credential attacks, privilege escalation, and lateral movement.

---

[← Back to Additional Skills](../README.md)
