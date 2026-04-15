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
















