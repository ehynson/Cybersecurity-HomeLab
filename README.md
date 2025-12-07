# Cybersecurity Homelab  
A full enterprise-style Active Directory and network segmentation lab built for hands-on IT and security experience

This repository documents the full build-out of a realistic corporate environment using VMware Workstation Pro, Windows Server 2022, Active Directory, Linux servers, Group Policy, segmentation, and security tooling.

The goal of this homelab is to practice:
- Systems administration  
- Identity and access management  
- Networking and segmentation  
- Windows + Linux server operations  
- SOC-style monitoring and security controls   

---

## **1. Homelab Overview**
This lab is structured to replicate a professional IT environment with:
- A dedicated Active Directory forest  
- Multiple isolated subnets  
- Workstations and servers  
- Logging and security layers   

---

## **2. Current Architecture**

### **Virtualization Platform**
- VMware Workstation Pro  
- Host OS: Windows 10/11  

### **Virtual Networks**
Two host-only networks were created:

| Network | Subnet | Purpose |
|--------|--------|---------|
| **VMnet1** | 192.168.10.0/24 | Active Directory network (DC + workstations) |
| **VMnet2** | 192.168.20.0/24 | Linux servers, service network |

- DHCP disabled on both  
- Manual IP assignments  
- VMnet2 allows host access for SSH/web testing  

---

## **3. Domain Controller (DC1)**

| Setting | Value |
|--------|-------|
| Hostname | **DC1** |
| OS | Windows Server 2022 Standard Evaluation (Desktop Experience) |
| IP | `192.168.10.10` |
| Role | Active Directory Domain Controller + DNS |
| Domain | **lab.local** |
| NetBIOS | **LAB** |
| Functional Level | Windows Server 2016 |

DC1 was promoted to the first domain controller in a new forest.

---

## **4. Active Directory Structure**

### **Organizational Units (OUs)**
```
01-Users
02-Computers
03-Servers
04-Groups
05-ServiceAccounts
06-IT
```

### **Users Created**
| Name | Username | Notes |
|------|----------|-------|
| John Doe | john.doe | Standard user |
| Alice Morgan | alice.morgan | Admin-track account |
| Eric IT | eric.it | Lab IT user |

### **Security Group**
```
IT-Admins (Global Security Group)
```

**Members:**
- alice.morgan  
- eric.it

---

## **5. Documentation Index**

All documentation is inside the `/docs` folder.

```
/docs
   01_Environment_and_Architecture.md
   02_ActiveDirectory_and_Users.md      (coming soon)
   03_GroupPolicy_Baseline.md           (coming soon)
   04_Windows_Workstation_Join.md       (coming soon)
   05_Linux_Server_Setup.md             (coming soon)
   06_Security_and_Logging.md           (coming soon)
```

Each file represents a clean step in the build process.

---

## **6. Goals for Future Phases**

### **Phase 2 — Windows Workstation Integration**
- Build Windows 10/11 VM  
- Join to domain  
- Apply baseline GPO  
- Test user logins and permissions  

### **Phase 3 — Linux Server Network**
- Deploy Ubuntu Server on VMnet2  
- Configure SSH, Nginx, firewall  
- Prepare for monitoring and security tools  

### **Phase 4 — Security Instrumentation**
- Sysmon deployment  
- Event log forwarding  
- SIEM (e.g., Wazuh/Elastic/Graylog)  
- Alerting rules  

---

## **7. Purpose**
This homelab serves as a full-cycle IT + cybersecurity portfolio project showcasing:

- AD administration  
- Enterprise networking  
- Security engineering  
- Infrastructure documentation  

It demonstrates the foundational skills expected of:
- Helpdesk  
- Junior Sysadmin  
- SOC Tier 1  
- Blue Team  

---

## **8. Author**
Built and documented by **Eric** as part of a structured cybersecurity learning and career development plan.

---

## **9. License**
This project is for personal and educational use.
