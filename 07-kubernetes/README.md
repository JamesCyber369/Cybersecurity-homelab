# ☸️ Phase 07 — Kubernetes Cluster (K3s)

**Status:** ✅ Complete

---

## 🎯 Goals

- Deploy a lightweight Kubernetes cluster using K3s
- Verify cluster node shows Ready status
- Deploy a test containerized application
- Establish foundation for future container-based workloads

---

## 🔍 What Is Kubernetes — In Plain Terms

Kubernetes automatically manages containerized applications. Instead of manually starting, stopping, and monitoring each application, Kubernetes handles all of that automatically.

In electrical terms: like a smart panel that automatically distributes and manages loads — you tell it what needs to run and it handles distribution, balancing, and recovery without manual intervention per circuit.

K3s is a lightweight version of Kubernetes designed for limited-resource environments — same features, fraction of the memory footprint.

---

## 🖥️ VM Specifications

| Setting | Value |
|---|---|
| **VM Name** | k3s-master |
| **OS** | Ubuntu Server 24.04.4 LTS |
| **CPU** | 2 cores |
| **RAM** | 2048 MiB |
| **Disk** | 20GB |
| **Network** | vmbr0 |
| **IP Address** | 10.0.0.66 |
| **Node Status** | Ready |

---

## 🔧 Deployment Process

K3s installed using the official one-line installer:

curl -sfL https://get.k3s.io | sh -

Verified cluster health:

sudo k3s kubectl get nodes

Output confirmed node status: Ready

Deployed test application:

sudo k3s kubectl create deployment nginx --image=nginx

sudo k3s kubectl get pods

Output confirmed pod status: Running

---

## ⚡ Electrical Mapping

| Kubernetes Term | Electrical Equivalent |
|---|---|
| Kubernetes cluster | Smart load management panel |
| Pod | Individual circuit running one specific load |
| Node | A physical panel in the overall system |
| Container | Self-contained appliance — plug in anywhere and it runs |
| Deployment | Standing load requirement — panel keeps it energized automatically |

---

## 📝 Still To Do

- Add worker nodes for a true multi-node cluster
- Deploy security-relevant workloads
- Connect Wazuh agent to monitor this node
- Practice RBAC and pod security policies

---

[← Phase 06](../06-wazuh-siem/README.md) | [Next: OpenStack →](../08-openstack-cloud/README.md)
