# <div align="center">FTP (vsFTPd 2.3.4) Enumeration & Exploitation</div>

<div align="center">
This target hosts an FTP service running vsFTPd 2.3.4, which was identified during enumeration and exploited using a known backdoor vulnerability to achieve unauthorized remote access.
</div>

<br>

<div align="center">
  <img width="350" height="350" src="https://github.com/user-attachments/assets/540ae502-d631-4182-a774-05188ad5ae14" />
</div>

---

## 1. FTP Reconnaissance using Nmap

### 🔍 Command Used

nmap -p- -sV -sC <target-ip>

### 📌 Explanation

- `-p-` → Scans all 65535 ports  
- `-sV` → Detects service versions running on open ports  
- `-sC` → Runs default Nmap scripts for enumeration  

### 🎯 Purpose

This scan helps identify open ports and running services on the target machine, allowing us to detect potential attack vectors.

### 📊 Key Finding

- Port 21/tcp → Open  
- Service → FTP  
- Version → vsFTPd 2.3.4  

👉 This version contains a known backdoor vulnerability, making it a high-priority target.

<p align="center">
  <img width="1047" height="507" src="https://github.com/user-attachments/assets/14035783-a71a-4c39-af62-b640ebc5faf1" />
</p>

---

## 2. Searching for Exploit in Metasploit

### 🔍 Command Used

msfconsole  
search vsftpd  

### 📌 Explanation

Metasploit is used to identify available exploits for the detected vulnerable service.

<p align="center">
  <img width="1046" height="685" src="https://github.com/user-attachments/assets/ea1aac17-4bdf-41d2-9096-b17e19824fc1" />
</p>

---

## 3. Selecting the Exploit

The following exploit module was selected:

`exploit/unix/ftp/vsftpd_234_backdoor`

👉 This exploit targets the backdoor present in vsFTPd 2.3.4.

<p align="center">
  <img width="607" height="91" src="https://github.com/user-attachments/assets/953ca857-8e96-45e4-b1c7-1ccc226ec712" />
</p>

---

## 4. Configuring Exploit Options

Command used:

options  

👉 This command displays required parameters such as RHOST.

<p align="center">
  <img width="872" height="166" src="https://github.com/user-attachments/assets/84fd3a7f-a232-475d-b848-57bf29231689" />
</p>

---

## 5. Exploitation

Command used:

exploit  

👉 The exploit was successfully executed, resulting in remote shell access.

<p align="center">
  <img width="867" height="672" src="https://github.com/user-attachments/assets/09f8052a-2457-48c3-9bc1-53d21e5bf285" />
</p>

---

## 6. Proof of Exploitation

To verify access, a directory was created on the target system and confirmed.

👉 This confirms successful remote command execution.

<p align="center">
  <img width="707" height="610" src="https://github.com/user-attachments/assets/499225a4-b0ed-48ee-9fc2-b1b45cecf48c" />
</p>

<p align="center">
  <img width="722" height="396" src="https://github.com/user-attachments/assets/f1940c05-3f2a-4dc1-aced-23bd3d2670ad" />
</p>

---

## 🚨 Impact

- Remote Code Execution (RCE) achieved  
- Unauthorized access to the target system  
- Potential for full system compromise  

---

## 🛠️ Remediation

- Upgrade vsFTPd to a secure version  
- Disable FTP service if not required  
- Use secure alternatives like SFTP  
- Restrict access using firewall rules  
