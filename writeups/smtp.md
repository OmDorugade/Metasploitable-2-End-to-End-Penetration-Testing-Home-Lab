# <div align="center">SMTP Enumeration & Exploitation</div>
<div align="center">
This target hosts a SMTP service running on port 25, which was identified during enumeration and exploited to gain unauthorized access.
</div>

<p align="center">
  <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/5674941d-9e59-4546-867e-b2da361257d3" />
</p>

## 1. SMTP Reconnaissance using Nmap

### 🔍 Command Used

nmap -p- -sV -sC <target-ip>

### 📌 Explanation

- `-p-` → Scans all 65535 ports  
- `-sV` → Detects service versions  
- `-sC` → Runs default scripts  

### 🎯 Purpose

Identify open services and detect SMTP running on port 25.

### 📊 Key Finding

- Port 25/tcp → Open  
- Service → SMTP  
- Server → Postfix (Ubuntu)  

👉 SMTP is available and can be used for user enumeration.

<p align="center">
  <img width="940" height="624" alt="image" src="https://github.com/user-attachments/assets/bcd73512-c79d-475f-b1d3-56e294e41a4e" />
</p>

## 2. Searching for SMTP Enumeration Module

### 🔍 Command Used

msfconsole  
search smtp  

### 📌 Explanation

Metasploit provides multiple SMTP-related modules; we focus on user enumeration.

<p align="center">
  <img width="940" height="513" alt="image" src="https://github.com/user-attachments/assets/503545e4-397e-4174-93b1-84af47ce378e" />
</p>

## 3. Selecting SMTP Enumeration Module

The following module was selected:

`auxiliary/scanner/smtp/smtp_enum`

👉 This module enumerates valid users via SMTP service.

<p align="center">
  <img width="940" height="327" alt="image" src="https://github.com/user-attachments/assets/c23f1599-a1ba-48c7-9f2c-e74d4ce8a295" />
</p>






