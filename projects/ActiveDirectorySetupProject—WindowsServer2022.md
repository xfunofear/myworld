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

<p align="center">
<img src="../images/SCR 1 _ System renamed to SRV-DC01.png" alt="SCR 1 _ System renamed to SRV-DC01.png" width="900"/>
</p>
---
<p align="center">
<img src="../images/SCR 2_Konfiguracja statycznego IP i zatwierdzenie.png" alt="SCR 2_Konfiguracja statycznego IP i zatwierdzenie.png" width="900"/>
</p>
---
<p align="center">
<img src="../images/SCR3 _ TIME ZONE.png" alt="SCR3 _ TIME ZONE.png" width="900"/>
</p>

### 2. Install AD DS Role

- Open Server Manager → Add Roles and Features
- Select `Active Directory Domain Services`
- Proceed with installation

<p align="center">
<img src="../images/scr4_Active Directory Domain Services.png" alt="scr4_Active Directory Domain Services.png" width="900"/>
</p>
---
<p align="center">
<img src="../images/SCR5_ INSTALL AD.png" alt="SCR5_ INSTALL AD.png" width="900"/>
</p>
---
### 3. Promote Server to Domain Controller

After installing the "Active Directory Domain Services" role, the server needs to be promoted to a Domain Controller.

🧭 Steps:

1. In **Server Manager**, click the **flag icon** (⚠️ in top bar) → select **"Promote this server to a domain controller"**.

<p align="center">
<img src="../images/SCR6 PROMOE THIS SERVER.png" alt="SCR6 PROMOE THIS SERVER.png" width="900"/>
</p>
---
2. In the **Deployment Configuration** step:
   - Select: `Add a new forest`
   - Root domain name: `lab.local`
   
<p align="center">
<img src="../images/SCR7_ LAB LOCAL.png" alt="SCR7_ LAB LOCAL.png" width="900"/>
</p>
---
3. In the **Domain Controller Options** step:
   - Leave default options checked: `Domain Name System (DNS)` and `Global Catalog (GC)`
   - Set the **Directory Services Restore Mode (DSRM)** password (you’ll need this for recovery scenarios)

<p align="center">
<img src="../images/SCR8 _ EKRAN USTAWIANIA HASLA.png" alt="SCR8 _ EKRAN USTAWIANIA HASLA.png" width="900"/>
</p>
---

4. Click **Next** through the remaining configuration steps (NetBIOS name, paths, review)

5. At the **Prerequisites Check** step:
   - Wait for validation to complete (warnings are OK)
   - Click **Install**

<p align="center">
<img src="../images/SCR9_ INSTALL.png" alt="SCR9_ INSTALL.png" width="900"/>
</p>
---
6. The server will automatically **reboot** after promotion.

7. After reboot, log in using domain credentials:
   - Username: `LAB\Administrator`
   - Confirm login via `whoami` in CMD:
     ```cmd
     whoami
     ```
     Should output:
     ```
     lab\administrator
     ```
<p align="center">
<img src="../images/SCR10 LOGOWANIE.png" alt="SCR10 LOGOWANIE.png" width="900"/>
</p>
---
<p align="center">
<img src="../images/scr11_whoami.png" alt="scr11_whoami.png" width="900"/>
</p>
---
### 4. Create Organizational Unit

- Open **Active Directory Users and Computers**
- Right-click domain → New → Organizational Unit
- Name: `Helpdesk`

<p align="center">
<img src="../images/scr12_adusers computers.png" alt="scr12_adusers computers.png" width="900"/>
</p>
---
<p align="center">
<img src="../images/scr13_helpdesk.png" alt="scr13_helpdesk.png" width="900"/>
</p>
---


### 5. Create User `jkowalski`

- Inside `Helpdesk` OU → New → User
- Name: Jan Kowalski, Username: `jkowalski`
- Password: `kowal1234`  
  ⬜ Uncheck "User must change password at next logon"

<p align="center">
<img src="../images/scr14_kowalski.png" alt="scr14_kowalski.png" width="900"/>
</p>
---
<p align="center">
<img src="../images/scr15_userzy.png" alt="scr15_userzy.png" width="900"/>
</p>
---



### 6. Create Security Group

- Inside `Helpdesk` OU → New → Group
- Name: `Helpdesk Team`, Type: Security, Scope: Global

<p align="center">
<img src="../images/scr16_group.png" alt="scr16_group.png" width="900"/>
</p>

---

### 7. Add User to Group

- Open group properties → Members → Add `jkowalski`
- Confirm membership

<p align="center">
<img src="../images/scr17_dodanie usera.png" alt="scr17_dodanie usera.png" width="900"/>
</p>

---

## ✅ Verification

Open Command Prompt (CMD):

```bash
whoami
