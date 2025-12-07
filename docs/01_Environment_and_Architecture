# Cybersecurity Homelab - Environment & Architecture Documentation

## **1. Overview**
This document describes the initial environment setup for a segmented, enterprise-style cybersecurity homelab. The goal of this phase is to establish a realistic IT foundation based on Windows Server Active Directory, isolated networks, and proper VM configuration.

The outcomes of this phase include:
- A functioning virtualization environment  
- Isolated lab networks  
- A fully deployed Domain Controller (DC1)  
- A clean and scalable Active Directory structure  

---

## **2. Host System and Virtualization**
**Virtualization Platform:** VMware Workstation Pro  
**Host OS:** Windows 10/11  
**Purpose:** Provide an isolated, reproducible environment for enterprise-level IT and cybersecurity workflows.

---

## **3. Virtual Network Architecture**

### **VMnet Configuration**
Two host-only networks were created using VMware Virtual Network Editor:

| Network | Type | Subnet | Notes |
|---------|------|---------|--------|
| **VMnet1** | Host-Only | **192.168.10.0/24** | Active Directory network (DC + workstation). Host adapter disabled. |
| **VMnet2** | Host-Only | **192.168.20.0/24** | Linux server network. Host adapter enabled for SSH/web access. |

### **Rationale**
- Host-only networks ensure complete isolation from the physical LAN.  
- Separate networks model real-world segmentation (internal AD zone vs service network).  
- No DHCP was enabled, all addressing is manually assigned to teach network administration fundamentals.  

---

## **4. Virtual Machine: DC1 (Domain Controller)**

| Setting | Value |
|--------|--------|
| **Name** | DC1 |
| **OS** | Windows Server 2022 Standard Evaluation (Desktop Experience) |
| **CPU/RAM** | 2 vCPUs / 5 GB RAM |
| **Disk** | 60 GB, thin provisioned |
| **Network Adapter** | Custom: VMnet1 |

### **IP Configuration**
Manually assigned static IP:

```
IP Address: 192.168.10.10
Subnet Mask: 255.255.255.0
Gateway: (none)
DNS Server: 127.0.0.1
```

### **Hostname**
```
DC1
```

### **Roles Installed**
- Active Directory Domain Services (AD DS)  
- DNS Server (installed automatically with AD DS)

### **Domain Configuration**
- **Domain name:** lab.local  
- **NetBIOS name:** LAB  
- **Functional level:** Windows Server 2016 (highest available for Server 2022)  

This completes the identity backbone of the homelab.

---

## **5. Active Directory Organizational Structure**

Custom Organizational Units (OUs) were created to follow best practices and avoid using the default system containers:

```
01-Users
02-Computers
03-Servers
04-Groups
05-ServiceAccounts
06-IT
```

### **Users Created**
| Full Name | Username | Notes |
|-----------|----------|-------|
| John Doe | john.doe | Standard user |
| Alice Morgan | alice.morgan | Admin-track user |
| Eric IT | eric.it | IT user for lab operations |

Each user was assigned a unique randomized strong password (not included in public documentation).

### **Group Created**
```
IT-Admins (Global Security Group)
```

**Members:**  
- alice.morgan  
- eric.it

---

## **6. Current State Summary**
At this stage of the project, the lab contains:

- A fully functional Windows Server 2022 Domain Controller  
- Proper DNS and AD forest initialization  
- A clean OU structure  
- Multiple test users and an admin group  
- Professional network segmentation using VMware  
- Documentation reflecting industry standards  

This establishes a strong baseline for the next phases:

- Preparing Group Policies  
- Building the Windows client VM and joining it to the domain  
- Configuring the Linux server environment  
- Introducing logging and security layers  

---

## **7. Next Steps**

### **Phase 2: Group Policy & Workstation Deployment**
- Configure baseline security policies  
- Create and install a Windows 10/11 workstation  
- Join the workstation to the domain  
- Validate AD functionality with user logins  

### **Phase 3: Linux Server Setup**
- Deploy Ubuntu Server  
- Configure essential services (SSH, Nginx, firewall)  
- Prepare server for monitoring and future SIEM integration  

This document marks the successful completion of Phase 1.
