<div align="center">

# 🏗️ CoreInfra

### Infrastructure Automation Toolkit for SMEs

**Deploy a complete Windows Server infrastructure in minutes — not days.**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![PowerShell](https://img.shields.io/badge/PowerShell-5.1+-blue?logo=powershell)](https://microsoft.com/powershell)
[![Terraform](https://img.shields.io/badge/Terraform-1.5+-purple?logo=terraform)](https://terraform.io)
[![Ansible](https://img.shields.io/badge/Ansible-2.15+-red?logo=ansible)](https://ansible.com)
[![Azure](https://img.shields.io/badge/Azure-Cloud-blue?logo=microsoftazure)](https://azure.microsoft.com)

</div>

---

## 🎯 What is CoreInfra?

CoreInfra is a fully automated infrastructure toolkit designed for **IT consultants and SMEs** who need to deploy a production-ready Windows Server environment on Azure — without spending weeks on manual configuration.

From Active Directory to Kubernetes, from CI/CD pipelines to security hardening, CoreInfra handles it all with a single command.

---

## ✨ Key Features

| Feature | Technology | Status |
|---------|-----------|--------|
| ☁️ Azure Infrastructure | Terraform | ✅ Production Ready |
| 🏛️ Active Directory | PowerShell | ✅ Production Ready |
| 🖥️ Hyper-V + VDI | PowerShell + Terraform | ✅ Production Ready |
| 🌐 IIS + SQL Server + Docker | PowerShell Direct | ✅ Production Ready |
| 🐧 Linux + Kubernetes | Ansible + k3s | ✅ Production Ready |
| ⚙️ CI/CD Jenkins | Docker | 📋 Planned |
| 🔒 CIS Hardening | Ansible | 📋 Planned |
| 📊 Monitoring | Prometheus + Grafana | 📋 Planned |
| 🛡️ Security (SIEM) | Defender + LAPS | 📋 Planned |

---

## 🏛️ Architecture

```
Azure Cloud
│
├── 🔒 Network Layer
│   ├── Virtual Network
│   ├── Subnet DC
│   └── Subnet Hyper-V
│
├── 🏛️ Domain Controller
│   ├── Active Directory Domain Services
│   ├── DNS Server
│   ├── DHCP Server
│   └── Custom domain
│
├── 🖥️ Hyper-V Host
│   ├── Hyper-V Role
│   ├── Remote Desktop Services
│   ├── Domain joined
│   └── 🖧 NAT Network (192.168.100.0/24)
│       ├── VM-IIS     → IIS + ASP.NET 4.5
│       ├── VM-SQL     → SQL Server 2022
│       ├── VM-Docker  → Docker CE 27.5.1
│       └── vm-linux01 → Ubuntu 22.04 + k3s
│
└── 💻 VDI Workstations
    ├── Workstation 01 (Windows 10 Enterprise)
    └── Workstation 02 (Windows 11 Enterprise)
```

---

## 🚀 Deployment Phases

### ✅ Phase 1 — Azure Infrastructure
Automated provisioning of all Azure resources via Terraform modules:
- Virtual Network + Subnets + NSGs
- Virtual Machines with managed disks
- Static public/private IPs

### ✅ Phase 2 — Active Directory
Full AD structure deployed via PowerShell in a single script:
- Domain promotion (lab.local)
- OUs: CORP, Users, Computers, Servers, Groups, ServiceAccounts
- Groups: GRP_Admins, GRP_IT, GRP_Finance, GRP_RH
- Password Security Policy (PSO): 12 chars, lockout after 5 attempts
- AD Sites: Paris-HQ, Lyon-Branch
- DHCP scopes for both sites

### ✅ Phase 3 — Hyper-V + VDI
- Hyper-V host configuration
- Virtual switches (External + Internal)
- Remote Desktop Services
- VDI workstations automatically joined to domain

### ✅ Phase 4 — Windows Applications
- VM-IIS : IIS + ASP.NET 4.5 (Windows Server 2022)
- VM-SQL : SQL Server 2022 RTM (16.0.1000.6)
- VM-Docker : Docker CE 27.5.1 + Windows Containers
- NAT network 192.168.100.0/24 via WinNAT

### ✅ Phase 5 — Linux + Kubernetes
- vm-linux01 : Ubuntu 22.04 LTS (guest Hyper-V — 192.168.100.20)
- k3s v1.34.5 — control-plane Ready
- Ansible 2.10 — control node
- SSH key authentication — no passwords
- Deployed via Ansible playbook (idempotent)

### 📋 Phase 6 — CI/CD
Jenkins pipeline in containers

### 📋 Phase 7 — Hardening
Ansible playbooks, CIS Benchmark compliance

### 📋 Phase 8 — Monitoring
Prometheus + Grafana dashboards

### 📋 Phase 9 — Security
Microsoft Defender, SIEM, LAPS password rotation

---

## 📦 Tech Stack

```
Infrastructure  │ Terraform 1.5+, Azure RM Provider
Automation      │ PowerShell 5.1+, Ansible 2.10+
Containers      │ Docker, k3s (Kubernetes)
CI/CD           │ Jenkins
Monitoring      │ Prometheus, Grafana
Security        │ Microsoft Defender, LAPS, CIS Benchmark
OS              │ Windows Server 2022, Windows 10/11 Enterprise, Ubuntu 22.04
```

---

## 📊 Deployment Results

After full deployment, CoreInfra delivers:

```
✅ Domain Controller     → Active Directory + DNS + DHCP
✅ Hyper-V Host          → Virtualization platform + RDS
✅ VDI Workstations      → Domain-joined Windows 10/11
✅ Application Servers   → IIS + SQL Server 2022 + Docker CE
✅ Linux + Kubernetes    → Ubuntu 22.04 + k3s cluster
✅ Security Policies     → PSO, lockout, password complexity
✅ Network Segmentation  → Subnets, NSGs, WinNAT routing
```

---

## 🔐 Access & Licensing

This repository is a **public showcase**. The full source code is available on request for:

- 🤝 **IT Consultants** looking to accelerate client deployments
- 🏢 **SMEs** needing a managed infrastructure solution
- 🎓 **Students & learners** building their homelab

📧 **Request access**: [Open an issue](https://github.com/MeriemAyari/CoreInfra-public/issues) or contact directly on [LinkedIn](https://linkedin.com/in/meriemayari)

---

## 🗺️ Roadmap

- [x] Phase 1 — Azure Infrastructure
- [x] Phase 2 — Active Directory
- [x] Phase 3 — Hyper-V + VDI
- [x] Phase 4 — Windows Applications (IIS, SQL, Docker)
- [x] Phase 5 — Linux + Kubernetes (Ubuntu 22.04 + k3s)
- [ ] Phase 6 — Jenkins CI/CD
- [ ] Phase 7 — Ansible Hardening
- [ ] Phase 8 — Prometheus + Grafana
- [ ] Phase 9 — Security (Defender, SIEM, LAPS)
- [ ] Web Interface + AI Integration

---

## 👩‍💻 Author

**Meriem Ayari** — Infrastructure & Cloud Automation Engineer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://tn.linkedin.com/in/meriem-ayari-2667a256)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/MeriemAyari)

---

<div align="center">

*Built with ❤️ for SMEs who deserve enterprise-grade infrastructure*

</div>