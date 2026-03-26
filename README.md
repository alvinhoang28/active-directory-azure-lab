# 🧪 Active Directory Home Lab (Microsoft Azure)

## 📌 Overview

This project demonstrates the setup and configuration of a cloud-based Active Directory environment using Microsoft Azure. The lab simulates real-world IT help desk tasks such as user account management, password resets, and domain authentication.

---

## 🎯 Objectives

* Deploy a Windows Server Domain Controller in Azure
* Configure Active Directory Domain Services (AD DS)
* Create and manage users, groups, and organizational units (OUs)
* Join a client machine to the domain
* Simulate common help desk tasks

---

## 🏗️ Lab Architecture

* **DC1** – Windows Server 2025 (Domain Controller)
* **CLIENT1** – Windows 10 (Domain-joined client)
* **Domain** – `mydomain.com`
* **Virtual Network** – AD-VNET

---

## ☁️ Technologies Used

* Microsoft Azure
* Active Directory Domain Services (AD DS)
* Windows Server 2025
* Windows 10
* Remote Desktop (RDP)
* PowerShell

---

## ⚙️ Setup Steps

### 1. Create Base Environment

* Created Resource Group: `AD-LAB`
* Created Virtual Network: `AD-VNET`
* Deployed VM: `DC1` (Windows Server 2025)

<img width="1388" height="447" alt="image" src="https://github.com/user-attachments/assets/3988eafa-1ca5-4b70-9567-5d2f7b30793d" />
<img width="1531" height="276" alt="image" src="https://github.com/user-attachments/assets/926337dd-fafa-40d9-a8bb-5f8d392641e9" />

---

### 2. Install Active Directory

Installed AD DS role and promoted server to Domain Controller:

```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools

Install-ADDSForest `
-DomainName "mydomain.com" `
-DomainNetbiosName "MYDOMAIN" `
-SafeModeAdministratorPassword (ConvertTo-SecureString "Password123!" -AsPlainText -Force) `
-InstallDNS
```

<img width="402" height="464" alt="image" src="https://github.com/user-attachments/assets/39b773ca-5345-49bf-93cf-71e2a0ce8700" />

---

### 3. Create Users & Organizational Units

* Created OUs:

  * IT
  * HR
  * Sales

* Created users:

  * Sam Ngo (IT)
  * Tiffany Vo (HR)

<img width="747" height="527" alt="image" src="https://github.com/user-attachments/assets/5d253101-64ef-4f49-9861-654f8af4c165" />
<img width="748" height="530" alt="image" src="https://github.com/user-attachments/assets/6d2a432f-d4ef-4923-8358-41c75157b903" />

---

### 4. Simulate Help Desk Tasks

Performed common IT support tasks:

* Password reset
* Account lock/unlock
* Added users to groups

<img width="753" height="528" alt="image" src="https://github.com/user-attachments/assets/e4220dc0-8a36-455a-aa67-6a1383fefd63" />
<img width="411" height="540" alt="image" src="https://github.com/user-attachments/assets/da60479b-6493-43e9-a312-d4e76e0466f7" />

---

### 5. Create Client Machine

* Deployed VM: `CLIENT1` (Windows 10)
* Connected to same virtual network

---

### 6. Join Client to Domain

* Configured DNS to point to Domain Controller
* Joined CLIENT1 to `mydomain.com`

<img width="302" height="152" alt="image" src="https://github.com/user-attachments/assets/b703455c-6f5f-48a3-bf23-e004511320b2" />

---

### 7. Domain User Login

* Logged into CLIENT1 using domain credentials:

```
MYDOMAIN\jane_admin
```

<img width="1916" height="1039" alt="image" src="https://github.com/user-attachments/assets/8ecca692-7bb8-417e-bb60-f61736391e60" />

---

## 🧪 Key Skills Demonstrated

* Active Directory administration
* User and group management
* Domain configuration and authentication
* Troubleshooting login and access issues
* Basic networking (DNS configuration)

---

## 🔍 Troubleshooting

Common issues encountered:

* Domain join failures due to incorrect DNS configuration
* RDP connectivity issues resolved via Azure NSG rules

---

## 📈 What I Learned

* How to deploy and configure a Domain Controller in a cloud environment
* How DNS impacts domain functionality
* How to simulate real-world help desk scenarios
* How to troubleshoot authentication and connectivity issues

---

## 🚀 Future Improvements

* Add Group Policy configuration
* Implement file server and permissions lab
* Automate user creation with PowerShell

---

