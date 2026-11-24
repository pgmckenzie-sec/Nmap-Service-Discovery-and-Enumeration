# Nmap-Service-Discovery-and-Enumeration
## Nmap Service Discovery and Enumeration

### Overview
Conducted network reconnaissance and service version detection using **Nmap** against a virtual enterprise lab environment. Identified and mapped critical infrastructure components, including a Windows Server 2019 Active Directory Domain Controller, a Windows 10 domain-joined workstation, and a Linux server. Enumerated network services to validate host functionality, develop an asset inventory, and assess the exposed attack surface.

### Command Used

```bash
nmap -sV 192.168.56.0/24
```

### Key Findings

#### Domain Controller (DC01 - 192.168.56.10)

Discovered a Windows Server 2019 Domain Controller hosting core Active Directory services:

| Port | Service | Purpose |
|------|----------|----------|
| 53 | DNS | Domain Name Resolution |
| 88 | Kerberos | Authentication |
| 135 | MSRPC | Remote Procedure Calls |
| 139 | NetBIOS | Legacy SMB Support |
| 389 | LDAP | Active Directory Queries |
| 445 | SMB | File Sharing & Authentication |
| 593 | RPC over HTTP | Remote Administration |
| 3268 | Global Catalog | Forest-wide AD Searches |
| 3389 | RDP | Remote Desktop Access |
| 5985 | WinRM | PowerShell Remoting |

**Domain Identified:** `MyLab.local`

---

#### Windows 10 Workstation (192.168.56.20)

| Port | Service |
|------|----------|
| 3389 | RDP |

Identified a domain-joined Windows workstation with Remote Desktop enabled.

---

#### Linux Server (192.168.56.40)

| Port | Service |
|------|----------|
| 22 | SSH |

Detected a Linux system running OpenSSH, providing secure remote administration capabilities.

---

#### Windows Host (192.168.56.1)

| Port | Service |
|------|----------|
| 135 | MSRPC |
| 139 | NetBIOS |
| 445 | SMB |
| 5357 | HTTPAPI |

Identified Windows networking services and SMB-related communication channels.

---

### Skills Demonstrated

- Network Discovery
- Service Enumeration
- Active Directory Reconnaissance
- Asset Identification
- Attack Surface Analysis
- Windows Infrastructure Assessment
- Linux Administration Awareness
- Security Monitoring Preparation

### Security Relevance

The scan successfully identified high-value assets and critical enterprise services, including Active Directory authentication infrastructure, remote administration interfaces, and file-sharing services. This assessment provides baseline visibility into the environment and supports threat hunting, vulnerability assessment, and SOC monitoring activities.

### Tools

- Nmap
- Kali Linux
- VMware Workstation
- Windows Server 2019
- Windows 10
- Ubuntu Linux

---

### Network Topology

```text
                    MyLab.local
                          |
               +-------------------+
               |       DC01        |
               | 192.168.56.10     |
               | AD / DNS / LDAP   |
               +---------+---------+
                         |
         +---------------+---------------+
         |                               |
+----------------+          +----------------------+
| Windows 10     |          | Ubuntu Linux Server  |
| 192.168.56.20  |          | 192.168.56.40        |
| RDP Enabled    |          | SSH Enabled          |
+----------------+          +----------------------+

                         |
                 +---------------+
                 | Windows Host  |
                 | 192.168.56.1  |
                 | SMB Services  |
                 +---------------+
```

### Resume Bullet

- Performed network reconnaissance and service enumeration using Nmap within an Active Directory lab environment, identifying DNS, Kerberos, LDAP, SMB, WinRM, RDP, and SSH services across Windows and Linux systems to map network assets and evaluate attack surface exposure.
