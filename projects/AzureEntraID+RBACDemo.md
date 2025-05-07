# 🔐 Azure Entra ID + RBAC Demo (Free Tier)

This project demonstrates practical usage of Microsoft Entra ID (formerly Azure AD) and Azure Role-Based Access Control (RBAC), all using the free Azure account. It simulates real-world identity and access management in a cloud environment.

## 🚀 Goals

- Learn to manage users and groups in Microsoft Entra ID
- Apply RBAC to control access to Azure resources
- Simulate least-privilege access with a test user
- Showcase practical cloud IAM concepts in a portfolio-friendly way

---

## 🧩 Step-by-step Summary

### ✅ Step 1: Created a Test User
- Added `testuser` to Microsoft Entra ID
- Used manual password reset for controlled login
  <p align="center">
<img src="../images/azure/1.jpg" alt="Created a Test User" width="900"/>
</p>


### ✅ Step 2: Created Security Groups
- Groups: `Admins`, `Developers`
- Assigned:
  - `testuser` → Developers
  - My global admin → Admins
<p align="center">
<img src="../images/azure/2.jpg" alt="Developers" width="900"/>
</p>
---
<p align="center">
<img src="../images/azure/3.jpg" alt="Admins" width="900"/>
</p>

### ✅ Step 3: Assigned Azure RBAC Role
- Role: `Reader` assigned to `Developers` at subscription level
- This allowed all group members to view (but not change) Azure resources
<p align="center">
<img src="../images/azure/4.jpg" alt="Assigned Azure RBAC Role" width="900"/>
</p>
---
<p align="center">
<img src="../images/azure/5.jpg" alt="Reader" width="900"/>
</p
  
### ✅ Step 4: Created Storage Account
- Name: `portfoliostorage123`
- Region: West Europe
- Resource Group: `rg-storage-test`
<p align="center">
<img src="../images/azure/6.jpg" alt="Created Storage Account" width="900"/>
</p
### ✅ Step 5: Added Role Assignment
- Go to **Subscriptions** > your subscription > **Access control (IAM)**
- Assigned role `Reader` and `Storage Blob Data Reader` to group `Developers`
- This allowed members to view storage accounts and access blobs
<p align="center">
<img src="../images/azure/7.jpg" alt="Added Role Assignment" width="900"/>
</p
---
<p align="center">
<img src="../images/azure/8.jpg" alt="Storage Blob Data Reader" width="900"/>
</p
--- 
<p align="center">
<img src="../images/azure/9.jpg" alt="Storage Blob Data Readerend" width="900"/>
</p
### ✅ Step 6: Created Blob Container
- Inside storage account, created container `documents`
- Public access level set to `Private (no anonymous access)`
<p align="center">
<img src="../images/azure/10.jpg" alt="Created Blob Container" width="900"/>
</p

### ✅ Step 7: Uploaded Test File
- Uploaded file `documents.txt` to the container
- File used for access control testing
<p align="center">
<img src="../images/azure/11.jpg" alt="Uploaded Test File" width="900"/>
</p

### ✅ Step 8: Verified Permissions with Test User
- Logged in as `test.user1`
- Accessed `documents.txt` successfully (read)
- Attempted to delete file → received **Permission Denied**
- Confirmed: RBAC restriction works as expected (least privilege)
<p align="center">
<img src="../images/azure/12.jpg" alt="testuser" width="900"/>
</p

<p align="center">
<img src="../images/azure/13.jpg" alt="Verified Permissions with Test User" width="900"/>
</p



---

## 👤 Test Scenario

- **Logged in as testuser**
- Verified access to storage
- Failed attempt to delete blob confirmed RBAC restrictions were enforced

---


---

## 🧠 Key Concepts Demonstrated

- Microsoft Entra ID user/group management
- Azure RBAC: roles, scopes, assignments
- Principle of least privilege
- Real-world cloud identity simulation — all on the free tier

---

## 📦 Tools Used

- Azure Portal (Free Tier)
- Microsoft Entra ID (formerly Azure AD)
- Azure Storage Account
- Azure RBAC

---

