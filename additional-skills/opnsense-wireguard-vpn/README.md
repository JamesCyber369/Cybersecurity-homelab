# 🔒 OPNsense WireGuard VPN Configuration

**Status:** ✅ Complete
**Category:** Gap-Closing Skill

---

## 🎯 Goals

- Configure WireGuard VPN on OPNsense firewall
- Generate client configuration for laptop connectivity
- Implement split-tunnel configuration for realistic deployment
- Verify VPN connectivity to lab network

---

## 🔍 What Is A VPN — In Plain Terms

A VPN creates an encrypted tunnel between two points on a network. In electrical terms: like running a dedicated, shielded conduit between two panels — traffic inside is protected from anything outside the conduit.

WireGuard is the modern VPN protocol — faster, simpler, and more secure than older protocols like IPSec or OpenVPN. It's increasingly the industry standard.

---

## 🔧 VPN Configuration

### OPNsense WireGuard Instance

| Setting | Value |
|---|---|
| **Instance Name** | HomeLabVPN |
| **Listen Port** | 51820 |
| **Tunnel Address** | 10.10.0.1/24 |
| **Protocol** | WireGuard (UDP) |

### Client Configuration (Split Tunnel)

| Setting | Value |
|---|---|
| **Client Address** | 10.10.0.2/32 |
| **Endpoint** | 10.0.0.87:51820 |
| **Allowed IPs** | 10.10.0.0/24, 192.168.1.0/24, 10.0.0.0/24 |
| **Tunnel Type** | Split tunnel |

---

## 🔧 Deployment Process

1. Navigated to VPN → WireGuard → Instances in OPNsense GUI
2. Created new WireGuard instance (HomeLabVPN) with listen port 51820 and tunnel address 10.10.0.1/24
3. Generated server key pair automatically through OPNsense
4. Used Peer Generator to create client configuration
5. Set endpoint to 10.0.0.87:51820 (OPNsense WAN address and WireGuard port)
6. Enabled WireGuard service and applied configuration
7. Installed WireGuard client on Windows laptop
8. Imported generated client config as .conf file
9. Modified AllowedIPs from 0.0.0.0/0 (full tunnel) to specific lab subnets (split tunnel)
10. Activated tunnel — confirmed internet connectivity maintained

---

## 🔍 Real Troubleshooting Log

### Issue 1 — Full Tunnel Broke Internet Access
Initial config used AllowedIPs = 0.0.0.0/0 which routes ALL traffic through the VPN. Since OPNsense NAT wasn't configured to forward general internet traffic, the laptop lost internet access immediately upon connecting.

**Resolution:** Changed AllowedIPs to only include lab-specific subnets (split tunnel). This routes only lab traffic through the VPN while all other internet traffic uses the normal connection — the correct configuration for this use case.

**Lesson:** Full tunnel vs split tunnel is a real design decision with real consequences. Full tunnel is more secure but requires the VPN gateway to handle all internet traffic. Split tunnel is more practical for lab/remote access scenarios.

---

## 🧠 Key Concepts

| Term | Plain Definition |
|---|---|
| **WireGuard** | Modern VPN protocol — faster and simpler than IPSec or OpenVPN |
| **Full Tunnel** | All traffic goes through VPN — more secure, requires VPN gateway to handle internet |
| **Split Tunnel** | Only specific traffic goes through VPN — more practical for remote access |
| **Peer** | A client device authorized to connect to the VPN |
| **AllowedIPs** | Defines which traffic gets routed through the VPN tunnel |

---

## ⚡ Electrical Mapping

| VPN Term | Electrical Equivalent |
|---|---|
| VPN tunnel | Dedicated shielded conduit between two panels |
| Split tunnel | A transfer switch — some circuits on VPN, others on normal feed |
| Full tunnel | All circuits routed through one protected path |
| WireGuard peer | An authorized connection point on the protected circuit |

---

[← Back to Additional Skills](../README.md)
