# 🖥️ Active Directory Lab – Domain Client Join (Windows 10)

This lab demonstrates how to configure a **Windows 10 client machine** and join it to an existing **Active Directory domain** (`lab.local`) hosted on a separate domain controller (Windows Server 2019).

---

## ⚙️ Lab Environment

| Component          | Configuration                      |
|--------------------|-------------------------------------|
| Virtualization     | VirtualBox                         |
| Domain Name        | `lab.local`                        |
| Domain Controller  | Already configured (`SERVER01`)    |
| Client Machine     | New Windows 10 VM (`CLIENT01`)     |
| Network            | Host-Only Adapter (`vboxnet0`)     |

---

## 🧱 Windows 10 VM Setup

### 1. Create the Virtual Machine

- Image: **Windows 10 Education ISO**
- Machine name: `CLIENT01`
- Username: `LocalAdmin`
- Password: `Client1234`
- Enable **Host-Only Adapter** in network settings:
  - Adapter: `vboxnet0`
  - DHCP: **Disabled**
- Set **static IP** and DNS:

IP: 192.168.41.11
Mask: 255.255.255.0
Gateway: 192.168.41.1 (optional)
DNS: 192.168.41.10 (your domain controller)

📸 *Screenshot: client-network-settings.png*

---

### 2. Rename the Computer

- Go to: **Settings** → **System** → **About**
- Rename to `CLIENT01`
- Reboot required

📸 *Screenshot: rename-client01.png*

---

### 3. Join Domain `lab.local`

- Open **System Properties** → Change settings → Join a domain
- Enter domain: `lab.local`
- Provide domain admin credentials (e.g. `Administrator`)
- Restart when prompted

📸 *Screenshot: domain-join-success.png*

---

### 4. Log in as Domain User

- At login screen, click **Other user**
- Enter:

Username: lab\jkowalski
Password: Kowal1234

yaml
Kopiuj
Edytuj

- Successfully logged into domain as `jkowalski`

📸 *Screenshot: logged-in-jkowalski.png*

---

## 📌 Summary

This lab demonstrates:

- Creating and configuring a Windows 10 VM for domain access
- Joining a machine to an existing Active Directory domain
- Logging in with a domain user managed from the domain controller
