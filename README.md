# osticket
<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo" width="200"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Cloud-Microsoft%20Azure-blue?logo=microsoftazure&logoColor=white" />
  <img src="https://img.shields.io/badge/OS-Windows%2010-0078D6?logo=windows&logoColor=white" />
  <img src="https://img.shields.io/badge/Web%20Server-IIS-lightgrey?logo=microsoft&logoColor=blue" />
  <img src="https://img.shields.io/badge/Database-MySQL-blue?logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/App-osTicket%20v1.15.8-orange?logo=helpdesk&logoColor=white" />
</p>

<h1 align="center">osTicket - Prerequisites and Installation 👩🏽‍💻</h1>

This tutorial demonstrates how to install and configure **osTicket v1.15.8** on a Windows 10 VM hosted in Microsoft Azure.  
It covers setting up IIS, PHP, MySQL, HeidiSQL, and completing the osTicket installation.

---

### 🎥 Video Demonstration
- [**YouTube: How To Install osTicket with Prerequisites**](https://www.youtube.com)

---

### 🧰 Environments and Technologies Used
- Microsoft Azure (Virtual Machines / Compute)
- Remote Desktop
- Internet Information Services (IIS)

### 💻 Operating System Used
- **Windows 10 (21H2)**

---

### ✅ List of Prerequisites
- Azure Virtual Machine (Windows 10, 4 vCPUs)
- Remote Desktop login access
- osTicket Installation Files
- IIS with CGI enabled
- PHP Manager for IIS
- IIS Rewrite Module
- MySQL Database (v5.5.62)
- Register PHP in IIS
- osTicket v1.15.8
- HeidiSQL

---

## 🛠️ Installation Steps

### Step 1: Create an Azure Virtual Machine
Create a **Windows 10 VM** with 4 vCPUs, name it `osticket-vm`, and create a username and password.  
<img width="700" alt="Azure VM" src="https://github.com/user-attachments/assets/01d2dee9-e759-4b39-9d0f-5879c7e7f14b"/>

### Step 2: Connect to the VM via Remote Desktop
Use the VM’s **Public IP address** to connect.  
<img width="600" alt="RDP Login" src="https://github.com/user-attachments/assets/2b2b5052-ddaa-4e35-a6f5-2974beb74981"/>

### Step 3: Download osTicket Installation Files
Unzip the `osTicket-Installation-Files.zip` onto your desktop and name the folder `osTicket-Installation-Files`.  
<img width="600" alt="Files" src="https://github.com/user-attachments/assets/eb6fae71-1eac-4690-b202-c003510a6939"/>

### Step 4: Enable IIS with CGI
**Control Panel → Programs → Turn Windows Features On or Off** → Check:
- Internet Information Services
- World Wide Web Services
- Application Development Features → **CGI**
<img width="350" alt="IIS Setup" src="https://github.com/user-attachments/assets/3ccbad3f-0437-4dc1-b6b4-5a51d309cb01"/>

### Step 5–8: Install PHP Manager, Rewrite Module, VC_redist, and PHP
Install each component from `osTicket-Installation-Files`, unzip PHP to `C:\PHP`.  
<img width="500" alt="PHP Setup" src="https://github.com/user-attachments/assets/f93a3a0c-30ef-449e-88a8-905071b59353"/>

### Step 9: Install MySQL 5.5.62
Select **Typical Setup → Launch Configuration Wizard → Standard Configuration** and set username/password. (root/root)  
<img width="400" alt="MySQL Setup" src="https://github.com/user-attachments/assets/109d1b0b-f8c2-4bd1-8dd2-cf9a5a32d818"/>

### Step 10: Register PHP in IIS
In IIS (Run as Admin) → PHP Manager → Register `php-cgi.exe` → Restart IIS.  
<img width="600" alt="Register PHP" src="https://github.com/user-attachments/assets/2086f773-27f0-4026-8730-0b4bb5db0d80"/>

### Step 11: Install osTicket v1.15.8
From osTicket-Installation-Files unzip osTicket-v1.15.8 and look for upload folder. Copy the **upload** folder into `C:\inetpub\wwwroot` and rename it to **osTicket**. Restart IIS.  
<img width="600" alt="osTicket Folder" src="https://github.com/user-attachments/assets/120b7ba8-5bef-4228-9864-4ac86e4a08ae"/>

### Step 12: Browse osTicket
In IIS → **Default Web Site → osTicket → Browse :80**  
<img width="600" alt="osTicket Browse" src="https://github.com/user-attachments/assets/3b90cfe2-c879-49d3-a64b-e47aff7bd6a3"/>

### Step 13: Enable PHP Extensions
Note some extentions on osTicket are not enabled. Go to IIS enable `php_imap.dll`, `php_intl.dll`, `php_opcache.dll` in PHP Manager.  
<img width="700" alt="PHP Extensions" src="https://github.com/user-attachments/assets/4e779c3a-d8e0-4099-846d-a3ceb68c3265"/>

### Step 14: Rename Configuration File
Rename:  
`C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php` →  
`C:\inetpub\wwwroot\osTicket\include\ost-config.php`  
<img width="600" alt="Rename Config" src="https://github.com/user-attachments/assets/a407798d-eb07-4936-8ff8-145412bb34ec"/>

### Step 15: Assign File Permissions
Right-click `ost-config.php` → **Properties → Security → Advanced → Disable Inheritance → Remove All → Add "Everyone" → Full Control**  
<img width="610" alt="Permissions" src="https://github.com/user-attachments/assets/9cc756a5-fc2e-4fe6-b26d-644e28e33699"/>

### Step 16: Configure osTicket in Browser
Fill in Helpdesk Name, Admin Email, etc.  
<img width="400" alt="Setup Form" src="https://github.com/user-attachments/assets/b1df63cf-993a-430d-a97c-f6b3f6a5340f"/>

### Step 17: Create MySQL Database with HeidiSQL
From osTicket-Installation-Files, install HeidiSQL. Connect to MySQL (`root/root`) → Create database **osTicket**.  
<img width="400" alt="HeidiSQL" src="https://github.com/user-attachments/assets/df632000-9f76-4836-8257-0ac5cd563fad"/>

### Step 18: Complete osTicket Setup
Database: `osTicket` | Username: `root` | Password: `root` → Click **Install Now!**  
<img width="400" alt="Install Complete" src="https://github.com/user-attachments/assets/5f649859-4d83-4123-9330-8dba70911bb3"/>

---

## 🎉 Installation Complete!
You now have **osTicket v1.15.8** successfully installed on your VM.  
<img width="500" alt="image" src="https://github.com/user-attachments/assets/0441f95f-b941-4b98-9451-8e8be64f15d5" />

**Next Steps:**
- Configure departments and agents  
- Set up SLAs  
- Enable email piping for full help desk functionality  

---

💡 *Created by [Your Name](https://www.linkedin.com/in/yvonne-nderitu-7a2513313)*  
🏷️ *Microsoft Azure | IIS | MySQL | PHP | osTicket | Help Desk Systems*
