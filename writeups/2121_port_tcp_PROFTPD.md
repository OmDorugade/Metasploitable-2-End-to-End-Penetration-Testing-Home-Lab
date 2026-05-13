# <div align="center">ProFTPD (Port 2121) Enumeration & Exploitation</div>

<div align="center">
This target exposes an FTP service running ProFTPD on port 2121. Weak credentials allowed successful authentication through brute-force enumeration using Metasploit’s FTP login scanner.
</div>

<div align="center">
  <img width="450" height="250" alt="image" src="https://github.com/user-attachments/assets/cd85e351-683b-4e7d-b116-55da888ba32f" />
</div>

## 1. FTP Reconnaissance using Nmap

## 🔍 Command Used

nmap -p- -sV -sC target-ip

### 📌 Explanation

- `-p-` → Scan all ports  
- `-sV` → Detect service versions  
- `-sC` → Run default scripts 

## 📊 Key Findings

- Port 2121 → FTP
- Service → ProFTPD 1.3.1

👉 Indicates an FTP service is accessible remotely.

<p align="center">





