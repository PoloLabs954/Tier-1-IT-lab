# Tier 1 IT Lab – Active Directory Basics (Microsoft Azure)

## 🎯 Lab Overview

This lab simulates real-world Tier 1 help desk tasks using a **Windows Server** virtual machine deployed in **Microsoft Azure**. The focus is on **Active Directory Domain Services (AD DS)** – a core skill for user management, password resets, and domain-joined computer support.

> I have no formal IT experience, so I built this lab to demonstrate hands-on skills. All work is documented below with screenshots and a help desk ticket simulation.

---

## ☁️ Lab Environment

| Component | Technology |
|-----------|------------|
| **Cloud Platform** | Microsoft Azure |
| **Virtual Machine** | Windows Server 2022 Datacenter (Azure VM) |
| **Role Installed** | Active Directory Domain Services (AD DS) |
| **Domain Name** | `lab.local` (or your chosen name) |
| **Admin Tools** | Active Directory Users and Computers (ADUC), PowerShell, Azure Portal |
| **Connectivity** | RDP over Azure NSG (port 3389 restricted to my IP) |

---

## 📋 Lab Tasks Completed (Tier 1 Scenarios)

| # | Task (Problem) | Solution | Screenshot |
|---|----------------|----------|-------------|
| 1 | Deploy Windows Server VM in Azure | Created B1s VM, opened RDP port in NSG | ![VM Creation](screenshots/01-azure-vm-creation.png) |
| 2 | Install Active Directory Domain Services | Added AD DS role via Server Manager | ![AD Install](screenshots/02-ad-ds-install.png) |
| 3 | Promote server to Domain Controller | Configured new forest `lab.local`, set DSRM password | ![Promote DC](screenshots/03-promote-dc.png) |
| 4 | Create Organizational Units (OUs) | Created `IT`, `HR`, `Users` OUs for organization | ![OUs](screenshots/04-ous-created.png) |
| 5 | Create user accounts | Made `John.Doe`, `Jane.Smith` in appropriate OUs | ![Create Users](screenshots/05-create-users.png) |
| 6 | Reset a forgotten password | Used ADUC to reset password → "User must change at next logon" | ![Password Reset](screenshots/06-password-reset.png) |
| 7 | Unlock a locked-out account | Found locked user in ADUC → Unlock button | ![Unlock Account](screenshots/07-unlock-account.png) |
| 8 | Verify domain join readiness | Confirmed DNS points to DC, tested `nslookup lab.local` | ![DNS Test](screenshots/08-dns-test.png) |

---

## 🧠 What I Learned

- How to install and promote a Windows Server to a Domain Controller
- Navigating **Active Directory Users and Computers (ADUC)**
- Creating OUs and organizing users for group policy application
- Resetting passwords and unlocking accounts – the #1 Tier 1 ticket
- Basic DNS role of a DC (client domain join depends on it)
- Cost awareness: deallocated the Azure VM after lab sessions

---

## 📄 Sample Help Desk Ticket

**Ticket #101**  
**Issue:** User calls – "I forgot my domain password and now my account is locked."  
**Action Taken:**  
1. Logged into DC via RDP  
2. Opened ADUC → Found user in `IT` OU  
3. Right-click → Reset password (set temp `P@ssw0rd123`)  
4. Checked "Unlock account" checkbox  
5. Instructed user to log in with temp password and change it  
**Resolution:** User successfully logged in. Ticket closed.  
**Time:** 8 minutes

*More tickets in [`LAB-REPORT.md`](LAB-REPORT.md)*

---

## 🧹 Cost Management

- Azure VM size: **B1s** (eligible for free tier / low cost)
- Lab duration: ~3 hours total
- VM **deallocated** after each session to stop billing
- Total estimated cost: < $1 (or $0 with Azure credits)

![VM Deallocated](screenshots/09-vm-deallocated.png)

---

## 🔗 Lab Reference

This lab was completed following the guide at:  
[Jake's Tech Labs – AD Basics](https://jakestechlabs.com/labs/ad-basics/step-1)

All screenshots and configurations are my own work, adapted for a cloud environment (Microsoft Azure instead of on-premises Hyper-V).

---

## 🚀 Why This Matters for a Tier 1 Role

- ✅ Active Directory is used by **90%+ of businesses** – this is directly transferable
- ✅ Using Azure shows **cloud familiarity** (many companies use Azure AD / Entra ID)
- ✅ Documentation proves I can **communicate technical steps** clearly
- ✅ Cost management shows **responsibility** with company resources

---

*Last updated: April 2026*  
*Portfolio lab – no professional experience yet, but building skills daily.*
