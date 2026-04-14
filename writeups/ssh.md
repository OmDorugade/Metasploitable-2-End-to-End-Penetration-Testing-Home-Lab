# <div align="center">SSH Enumeration & Exploitation</div>

<div align="center">
This target hosts an SSH service running on port 22, which was identified during enumeration and exploited to gain unauthorized access through weak credentials.
</div>

<p align="center">
  <img width="350" height="350" alt="image" src="https://github.com/user-attachments/assets/cc54d9f8-bfae-485e-911f-fb64e05ea688" />
</p>

## 1. SSH Reconnaissance using Nmap

### 🔍 Command Used

nmap -p- -sV -sC <target-ip>

### 📌 Explanation

- `-p-` → Scans all 65535 ports  
- `-sV` → Detects service versions running on open ports  
- `-sC` → Runs default Nmap scripts for enumeration  

### 🎯 Purpose

This scan helps identify open ports and services, highlighting SSH as a potential entry point.

### 📊 Key Finding

- Port 22/tcp → Open  
- Service → SSH  
- Version → OpenSSH 4.7p1 Debian  

👉 SSH is accessible and may be vulnerable to credential-based attacks.

<p align="center">
  <img width="900" height="564" alt="image" src="https://github.com/user-attachments/assets/7bdede0a-c19f-49fa-a72f-875c631c8cb1" />
</p>

## 2. Searching for SSH Module in Metasploit

### 🔍 Command Used

msfconsole  
search ssh_login  

### 📌 Explanation

Metasploit provides an auxiliary module for performing SSH brute-force attacks using username and password lists.

<p align="center">
  <img width="940" height="718" alt="image" src="https://github.com/user-attachments/assets/8aeafc4b-2ee8-4ef7-b21e-d6bd56f5dbb5" />
</p>

## 3. Selecting the Module

The following module was selected:

`auxiliary/scanner/ssh/ssh_login`

👉 This module performs SSH login attempts using supplied credentials.

## 4. Configuring Module Options

### 🔍 Commands Used

options  

set RHOSTS <target-ip>  
set USER_FILE /home/kali/Desktop/ssh_user  
set PASS_FILE /home/kali/Desktop/ssh_password  
set VERBOSE true  
set STOP_ON_SUCCESS true  

### 📌 Explanation

- `USER_FILE` → Contains list of usernames  
- `PASS_FILE` → Contains list of passwords  
- `VERBOSE` → Displays each login attempt  
- `STOP_ON_SUCCESS` → Stops after finding valid credentials  

<p align="center">
  <img width="940" height="327" alt="image" src="https://github.com/user-attachments/assets/db794a6f-e866-442e-a3e4-06458ea0988a" />
</p>


## 5. Brute Force Execution

### 🔍 Command Used

exploit  

### 📊 Result

👉 Valid credentials discovered:

- Username: `msfadmin`  
- Password: `msfadmin`  

👉 SSH session successfully established.

<p align="center">
  <img width="940" height="454" alt="image" src="https://github.com/user-attachments/assets/ae99d7b2-2773-4b11-bd30-b7eb509650e2" />
</p>














