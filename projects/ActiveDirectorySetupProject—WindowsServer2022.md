# 🧠 Active Directory Setup Project — Windows Server 2022

This project demonstrates how to set up a basic Active Directory Domain Services (AD DS) environment using Windows Server 2022. It includes user and group creation, organizational unit (OU) design, and verifies working domain-level authentication.

---
## 🎯 Objective

The goal is to create a simple domain-based infrastructure to showcase basic knowledge of:

- Active Directory Domain Services (AD DS)
- Domain controller configuration
- Creating and managing users, groups, and OUs
- Role-based group memberships

---

## 🛠️ Environment

| Component | Details |
|----------|---------|
| OS | Windows Server 2022 |
| Server Name | `SRV-DC01` |
| Static IP | `192.168.1.10` |
| Domain | `lab.local` |
| Administrator | `LAB\Administrator` |
| User | `jkowalski` (Password: `Kowal1234`) |

---

## 🔧 Setup Steps

### 1. Initial Server Configuration

- Set static IP, hostname, and time zone
- Rename server to `SRV-DC01`
- Reboot after network changes

📸 `screenshots/server-manager-role.png`
<p align="center">
<img src="../images/SCR 1 _ System renamed to SRV-DC01.png" alt="SCR 1 _ System renamed to SRV-DC01.png" width="900"/>
</p>
---

### 2. Install AD DS Role

- Open Server Manager → Add Roles and Features
- Select `Active Directory Domain Services`
- Proceed with installation

📸 `screenshots/server-manager-role.png`

---

### 3. Promote Server to Domain Controller

- Create new forest: `lab.local`
- Set Directory Services Restore Mode (DSRM) password
- Reboot after promotion
- Log in as `LAB\Administrator`

📸 `screenshots/promotion-summary.png`  
📸 `screenshots/whoami-lab-admin.png`

---

### 4. Create Organizational Unit

- Open **Active Directory Users and Computers**
- Right-click domain → New → Organizational Unit
- Name: `Helpdesk`

📸 `screenshots/aduc-ou-helpdesk.png`

---

### 5. Create User `jkowalski`

- Inside `Helpdesk` OU → New → User
- Name: Jan Kowalski, Username: `jkowalski`
- Password: `kowal1234`  
  ⬜ Uncheck "User must change password at next logon"

📸 `screenshots/aduc-user-jkowalski.png`

---

### 6. Create Security Group

- Inside `Helpdesk` OU → New → Group
- Name: `Helpdesk Team`, Type: Security, Scope: Global

📸 `screenshots/aduc-group-members.png`

---

### 7. Add User to Group

- Open group properties → Members → Add `jkowalski`
- Confirm membership

📸 `screenshots/aduc-group-members.png`

---

## ✅ Verification

Open Command Prompt (CMD):

```bash
whoami
