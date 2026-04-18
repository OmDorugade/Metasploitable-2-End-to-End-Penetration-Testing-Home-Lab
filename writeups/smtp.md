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
  <img width="1352" height="38" alt="image" src="https://github.com/user-attachments/assets/94da571d-756f-4873-b7a9-2e7e8c3916bc" />
</p>

## 4. Configuring Module Options

### 🔍 Commands Used

options  

set RHOSTS <target-ip>  

### 📌 Explanation

- `RHOSTS` → Target IP address  
- Default wordlist is used for username enumeration  

<p align="center">
  <img width="1343" height="427" alt="image" src="https://github.com/user-attachments/assets/82e576d0-02e5-4020-9986-8723f62f8c63" />
</p>

## 5. Running SMTP Enumeration

### 🔍 Command Used

exploit  

<p align="center">
  <img width="940" height="126" alt="image" src="https://github.com/user-attachments/assets/03a070bc-51a1-4a90-b127-6145a3dc2120" />
</p>

### 📊 Result

👉 Discovered valid users:

- root  
- msfadmin  
- postgres  
- mysql  
- user  
- backup  
- www-data  
- daemon  

👉 These usernames can be used for further attacks (SSH, FTP, etc.).

<p align="center">
  <img width="940" height="275" alt="image" src="https://github.com/user-attachments/assets/9c2f061a-9a30-4119-a8b3-cbfbd9102a47" />
</p>

## 6. Commands Used where from :
<p align="center">
  <img width="940" height="763" alt="image" src="https://github.com/user-attachments/assets/2b9c682f-b225-4718-8675-69b113f59dc1" />
</p>

## 🚨 Impact

- Valid usernames disclosed  
- Enables brute-force attacks (SSH, FTP)  
- Helps in privilege escalation and lateral movement  

















