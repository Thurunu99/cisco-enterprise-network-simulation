# Multi-VLAN Enterprise Network Simulation 🌐

A fully segmented, secure, and redundant enterprise network design implemented using **Cisco Packet Tracer**.

---

## 📐 Architecture Overview

This project simulates a university enterprise network utilizing a 3-tier hierarchical model (Core, Distribution/Access) with high availability and granular security controls.

### Key Features
- **Network Segmentation**: 7 Isolated VLANs (Admin, Lecturers, Students, IT, Library, Finance, Server Farm).
- **Inter-VLAN Routing**: Configured using Router-on-a-Stick (802.1Q Encapsulation).
- **Dynamic Routing**: OSPF Area 0 enabled across core routers and layer 3 boundaries.
- **Services**: Centralized DHCP pools for clients and Static IPv4 for Enterprise Servers (Web, DNS, File).
- **Security Controls**: Extended Access Control Lists (ACLs), Port Security (Sticky MAC), DHCP Snooping, and SSH v2 management.

---

## 🛠️ Network Addressing Scheme

| VLAN ID | Subnet / Segment | Gateway IP | Purpose |
| :--- | :--- | :--- | :--- |
| **VLAN 10** | `192.168.10.0/24` | `192.168.10.1` | Administration |
| **VLAN 20** | `192.168.20.0/24` | `192.168.20.1` | Lecturers |
| **VLAN 30** | `192.168.30.0/24` | `192.168.30.1` | Students |
| **VLAN 40** | `192.168.40.0/24` | `192.168.40.1` | IT Infrastructure |
| **VLAN 50** | `192.168.50.0/24` | `192.168.50.1` | Library |
| **VLAN 60** | `192.168.60.0/24` | `192.168.60.1` | Finance |
| **VLAN 70** | `192.168.70.0/24` | `192.168.70.1` | Enterprise Servers |

---

## 🔐 Security Policy Implementation

1. **Access Control Lists (ACLs)**:
   - Student VLAN (`VLAN 30`) is restricted from accessing internal admin/finance subnets.
   - Student access is strictly permitted towards the Server Farm (`192.168.70.0/24`).

2. **Layer 2 Security**:
   - **Port Security**: Applied on access ports with dynamic sticky MAC assignment and violation mode set to restrict.
   - **DHCP Snooping**: Configured with trusted interfaces towards DHCP servers to prevent rogue DHCP attacks.
   - **SSH v2**: Disabled Telnet and enabled encrypted SSH management with RSA keys.

---

## ✅ Verification & Testing

- **Inter-VLAN Communication**: Tested ping reachability between authorized subnets.
- **Web Access Verification**: Successfully loaded web server default pages from client endpoints.
- **ACL Verification**: Confirmed traffic rejection from Student VLAN to Administrative subnets.
