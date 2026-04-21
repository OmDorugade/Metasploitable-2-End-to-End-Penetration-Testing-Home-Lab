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

## 2. HTTP Version Detection using Metasploit

### 🔍 Command Used

msfconsole  
search http_version  
use auxiliary/scanner/http/http_version  
set RHOSTS <target-ip>  
run  

### 📌 Explanation

This module confirms the HTTP service and extracts detailed version information.

<p align="center">
  <img width="940" height="551" alt="image" src="https://github.com/user-attachments/assets/ddd057aa-3230-4089-8cc5-4eac162b0c45" />
</p>

## 3. Searching for Exploits

### 🔍 Command Used

searchsploit apache php 5.2.4  

### 📌 Explanation

Search for known vulnerabilities affecting Apache + PHP combination.

### 📊 Result

- PHP CGI Argument Injection (CVE-2012-1823)  
👉 Allows remote code execution via crafted HTTP requests.

<p align="center">




















