# <div align="center">HTTP (Apache 2.2.8 + PHP 5.2.4) Enumeration & Exploitation</div>
<div align="center">
This target hosts a vulnerable HTTP service running Apache 2.2.8 with PHP 5.2.4, identified during enumeration. The outdated PHP CGI component was exploited using a known argument injection vulnerability to achieve remote code execution.
</div>

<div align="center">
  <img width="450" height="350" alt="image" src="https://github.com/user-attachments/assets/d82bfb5a-1a6f-4c2e-9c55-6b8fd526fc2e" />
</div>

## 1. HTTP Reconnaissance using Nmap

### 🔍 Command Used

nmap -p- -sV -sC <target-ip>

### 📌 Explanation

- `-p-` → Scans all 65535 ports  
- `-sV` → Detects service versions  
- `-sC` → Runs default scripts  

### 🎯 Purpose

Identify web services and versions running on the target system.

### 📊 Key Findings

- Port 80/tcp → Open  
- Service → HTTP  
- Server → Apache httpd 2.2.8 (Ubuntu) DAV/2  
- PHP Version → 5.2.4  

👉 This outdated stack is vulnerable to PHP CGI argument injection.

<p align="center">
  <img width="917" height="111" alt="image" src="https://github.com/user-attachments/assets/c4d0a582-89c1-45b0-bd29-77e3479f8fd4" />
</p>





