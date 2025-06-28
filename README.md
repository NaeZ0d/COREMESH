# COREMESH

COREMESH is a hands-on homelab project simulating an enterprise network environment. It includes Active Directory, VLAN segmentation, VPN/DNS filtering, SIEM monitoring, honeypots, and automation tools designed to enhance practical IT and cybersecurity skills across Windows, Linux, and ARM platforms.

---

## COREMESH Homelab Project

### Project Purpose

The COREMESH Homelab is designed to simulate a real-world enterprise network environment focused on building practical skills in IT infrastructure, cybersecurity operations, and network management. This project serves as a hands-on learning platform to explore Active Directory, network segmentation, security monitoring, automation, and incident response workflows.

### Project Goals

- Establish a robust Active Directory domain and file sharing infrastructure  
- Implement network segmentation with VLANs and secure remote access (VPN)  
- Build a Security Operations Center (SOC) lab environment with real-time monitoring and threat detection  
- Develop proficiency in Linux and Windows server administration, security tools, and scripting automation  
- Integrate hybrid cloud elements to simulate modern enterprise environments  
- Document and automate deployments to build a professional, scalable lab portfolio  

---

## Hardware & Roles

### Dell OptiPlex 3050 Micro (4 cores, 12GB RAM)  
**Role:** Lightweight Core Infrastructure  
- 1 core reserved for host OS, 3 cores for VMs  
- Runs core services with minimal CPU load  

| VM Name          | vCPU | RAM  | Purpose                                 |
|------------------|-------|------|-----------------------------------------|
| DC01             | 1     | 2GB  | Active Directory, DNS, DHCP             |
| FS01             | 1     | 2GB  | File Server (SMB storage)                |
| LocalUser (opt.) | 1     | 1GB| Management/Local admin VM (usually off) |



---


### Dell OptiPlex 7050 Micro (4 cores, 16GB RAM)  
**Role:** Security VM Host  
- 1 core reserved for host OS, 3 cores for VMs  

| VM Name          | vCPU | RAM | Purpose                                |
|------------------|-------|-----|----------------------------------------|
| FW01             | 1     | 2GB | Firewall (pfSense/OPNsense) & VLANs    |
| Kali Linux Purple | 1     | 3GB | Red/Purple team penetration testing    |
| Nessus  | 1     | 4GB | Nessus Vulnerability Scanner        |
| Rocky Linux  | 1     | 2GB | Linux IAM        |



---


### Beelink Mini PC (10 cores, 12 threads, 16GB RAM)  
**Role:** Main VM Host + DB Server  
- 2 cores reserved for host OS, 8 cores for VMs  

| VM Name               | vCPU | RAM | Purpose                                 |
|-----------------------|-------|-----|-----------------------------------------|
| SQL01                 | 1     | 2GB | MySQL/MariaDB backend                   |
| SIEM01                | 3     | 6GB | SIEM platform (ELK or Wazuh)            |
| SecurityAnalytics01   | 2     | 4GB | Graylog, TheHive, or FleetDM dashboards |
| Suricata   | 1     | 2GB | IPS(incline), Lower traffic volumes |
| Snort   | 1     | 2GB | IDS(passive), Basic packet monitoring |



---


### Raspberry Pi 4B (8GB RAM)  
**Role:** Blue Team Utility Node (DNS Filtering + VPN Gateway)  

- RAM: 8GB  
- Storage: MicroSD (OS) + USB 3.0 connected 1TB HDD/SSD (optional)  
- Network: Gigabit Ethernet  

**Services:**  
- Pi-hole / AdGuard Home for DNS filtering  
- WireGuard VPN Server for secure remote access  
- Optional: Syslog-ng / rsyslog log aggregation  
- Optional: Cowrie honeypot for SSH/telnet deception  

**Learning Opportunities:**  
- Network filtering and VPN setup  
- Log collection and forwarding to SIEM  
- Lightweight monitoring and deception  


---


### Raspberry Pi 5 (16GB RAM, 1TB NVMe)  
**Role:** Security Operations Node (SOC-in-a-Box)  

- RAM: 16GB  
- Storage: 1TB NVMe SSD  

**Services:**  
- Dockerized SOC stack: TheHive, Cortex, MISP, FleetDM  
- Arkime for full packet capture and PCAP indexing  
- Filebeat / Elastic Agent log forwarding  
- IntelOwl / MISP for IOC ingestion and enrichment  
- Security automation scripts (Python, Bash)  
- Static malware analysis tools (YARA, ClamAV, peframe)  
- Backup node for FS01 and SIEM exports  

**Learning Opportunities:**  
- SOC toolchain management and orchestration  
- Network forensics and threat intelligence  
- Automation and incident response workflows  


