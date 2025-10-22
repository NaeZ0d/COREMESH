# COREMESH

COREMESH is a hands-on homelab project simulating a full-scale enterprise network environment. It integrates Active Directory, VLAN segmentation, routing and switching, VPN and DNS filtering, network traffic monitoring, firewall configuration, and SIEM logging to build real-world IT, networking, and cybersecurity skills. The lab also incorporates honeypots, log analysis, and automation tools across Windows, Linux, and ARM-based platforms, providing comprehensive experience in network design, segmentation, and threat detection within a secure multi-VLAN infrastructure.

---

## COREMESH Homelab Project

### Project Purpose

The COREMESH Homelab is designed to simulate a real-world enterprise network environment focused on building practical skills in IT infrastructure, cybersecurity operations, and network management. This project serves as a hands-on learning platform to explore Active Directory, network segmentation, security monitoring, automation, and incident response workflows.

### Project Goals:

- Deploy a robust Active Directory domain and centralized file-sharing infrastructure to simulate enterprise identity and access management.
- Implement advanced network segmentation using VLANs, routing, and firewall policies to enforce layered security and traffic isolation.
- Configure secure remote access (VPN) and DNS filtering for controlled connectivity and endpoint protection.
- Build a fully functional Security Operations Center (SOC) environment featuring real-time monitoring, SIEM integration, intrusion detection/prevention, and honeypot analysis.
- Develop hands-on expertise in Linux and Windows server administration, network configuration, security tools, and scripting automation.
- Incorporate hybrid cloud components to emulate modern corporate infrastructure and identity federation scenarios.
- Automate, document, and version-control deployments to maintain a professional, scalable, and reproducible homelab portfolio.

---

## 🧩 COREMESH Homelab — Hardware & System Roles

**Overview:**  
COREMESH is an enterprise-grade homelab environment designed to emulate real-world **networking, systems administration, and cybersecurity operations**.  
It includes **Active Directory, VLAN segmentation, firewall security, VPN, SIEM monitoring, honeypots**, and **network scanning/management systems**.  
The lab is built across **Windows and Linux platforms** using a combination of **Dell OptiPlex, Beelink, GMKtec, and GL.iNet hardware**.

---

# 🖥️ COREMESH Homelab Hardware & Network Overview

## Hardware Inventory

| Device | Model | Specs | Primary Role | Notes |
|:-------|:-----|:-----|:------------|:-----|
| **GMKtec Mini PC** | COREMANAGE | Ryzen 7 / 32GB RAM | Management Node | Network control, automation, central management |
| **GMKtec NucBox5** | CMESHNAS | Ryzen 5 / 16GB RAM | NAS / File Server Host | TrueNAS Core (FS01), shared storage, domain file repository |
| **Beelink Mini PC** | CMESHSecurity | Ryzen 7 / 32GB RAM | Security Node | IDS/IPS (IPS01), Security Linux (SEC-LNX01), threat analysis |
| **Dell OptiPlex 7050** | CMESHScanner | i7 / 32GB RAM | Scanning / Testing Node | Vulnerability & network scanning (Nessus, OpenVAS) |
| **Dell OptiPlex 3050** | CMESHAD | i5 / 16GB RAM | Domain Infrastructure Host | AD Domain Controller (DC01), Management Linux (MGMT-LNX01) |
| **TP-Link TL-SG108E** | Managed Switch | – | Network Switch | VLAN segmentation & trunk support |
| **GL.iNet Router** | OpenWrt | – | Edge Router | Internet gateway, upstream connectivity |
| **pfSense Firewall** | VM / Physical | FreeBSD-based | Firewall / VPN | Network firewall, VLAN routing, VPN gateway |

---

## Core Network Roles & Services

| Role | Host Device | OS / Platform | VLAN | Description |
|:----|:-----------|:------------|:----|:-----------|
| **DC01** | Dell 3050 (CMESHAD) | Windows Server | VLAN 201 | Active Directory, DNS, DHCP |
| **FS01 (TrueNAS)** | GMKtec NucBox5 | TrueNAS Core | VLAN 201 | File sharing, backups, GPO repository |
| **MGMT-LNX01** | Dell 3050 (CMESHAD) | Ubuntu Server | VLAN 201 | Network monitoring, management tools |
| **VULNCLIENT** | VM | Linux (Metasploitable) | VLAN 301 | Vulnerable host for penetration testing |
| **W11 Client** | VM | Windows 11 | VLAN 301 | Domain-joined user endpoint |
| **KALI/ATK1** | Dell 7050 | Kali Linux | VLAN 301 | Attack / red-team simulation |
| **IPS01** | Beelink Mini PC | Suricata / Snort | VLAN 401 | Intrusion Detection / Prevention System |
| **SEC-LNX01** | Beelink Mini PC | Ubuntu / Security Stack | VLAN 401 | Security operations, log parsing, packet analysis |
| **NGRFW01** | Beelink Mini PC | pfSense / OPNsense | VLAN 401 | Next-gen firewall testing instance |
| **SIEM01** | Beelink Mini PC | Ubuntu + ELK/Wazuh | VLAN 501 | Central logging, alerting, dashboards |
| **Nessus01** | Dell 7050 | Nessus / OpenVAS | VLAN 501 | Network and vulnerability scanning |
| **HPOT01** | Beelink Mini PC | Ubuntu / Cowrie | VLAN 601 | SSH honeypot for attacker detection |
| **HPOT02** | Beelink Mini PC | Ubuntu / Dionaea | VLAN 601 | Malware interaction honeypot |

---

## VLAN & Subnet Layout

| VLAN | Name | Subnet | Gateway | Purpose |
|:----|:----|:------|:-------|:-------|
| **101** | Hosts | 10.0.10.96/27 | 10.0.10.97 | Physical hosts & hypervisors |
| **201** | Admin / Management | 10.0.20.0/28 | 10.0.20.1 | Domain, NAS, management systems |
| **301** | Client / Attacker | 10.0.30.0/27 | 10.0.30.1 | User endpoints & attack simulation |
| **401** | Security | 10.0.40.0/29 | 10.0.40.1 | Firewall, IDS/IPS, security tools |
| **501** | Monitoring | 10.0.50.0/28 | 10.0.50.1 | SIEM, scanners, log monitoring |
| **601** | Honeypot | 10.0.60.0/30 | 10.0.60.1 | Isolated honeypot segment |


### ⚙️ Technologies & Skills Practiced

- **Networking:** VLAN trunking, routing, subnetting, firewall rules, VPN setup, DNS filtering  
- **System Administration:** Windows Server (AD, GPOs), Linux (Ubuntu, Debian), TrueNAS file management  
- **Cybersecurity:** SIEM (Wazuh/ELK), IDS/IPS (Suricata, Snort), honeypots, Nessus scanning, SOC monitoring  
- **Network Analysis:** Wireshark, tcpdump, packet capture, and log correlation  
- **Automation:** Bash, PowerShell, and Python scripting for system setup and alerting workflows  
- **Infrastructure Design:** Layered network segmentation, secure VLAN routing, and hybrid SOC simulation  

---

### 🧠 Future Enhancements

- Add **Zero Trust and NAC policies** (802.1X, RADIUS integration)  
- Expand **cloud integration** (Azure AD, Entra ID, Sentinel test workspace)  
- Introduce **containerized services (Docker Compose / Portainer)** for SOC tools  


---

## 🗺️ Network Topology

### COREMESH Logical Network Diagram

![COREMESH Logical Diagram](docs/Network%20Diagram/COREMESH_Logical%20Diagram.png)

> *COREMESH multi-VLAN architecture featuring firewall, security, monitoring, and honeypot layers.*

---

