# <div align="center">[FTP Enumeration & Exploitation]</div>
<div align="center">This target hosts an FTP service running vsFTPd 2.3.4, which was identified and exploited to achieve unauthorized remote access through a known backdoor vulnerability.
</div>
<br>
<div align="center">
  <img width="350" height="350" alt="image" src="https://github.com/user-attachments/assets/540ae502-d631-4182-a774-05188ad5ae14" />
</div>

## 1. FTP Reconnaissance using Nmap

###  Command Used

nmap -p- -sV -sC <target-ip>

###  Explanation

- -p- → Scans all 65535 ports  
- -sV → Detects service versions running on open ports  
- -sC → Runs default Nmap scripts for basic enumeration  

###  Purpose

This scan is performed to identify open ports and detect services running on the target machine. It helps in discovering potential attack vectors, such as vulnerable services like FTP.

###  Key Finding

- Port 21/tcp → Open  
- Service → FTP  
- Version → vsFTPd 2.3.4  

 This version is known to contain a backdoor vulnerability, making it a high-priority target for exploitation.

<p alig="center">
  <img width="1047" height="507" alt="image" src="https://github.com/user-attachments/assets/14035783-a71a-4c39-af62-b640ebc5faf1" />
</p>

## 2. Start msfconsole and search the version name vsftpd.

###  Command Used

msfconsole

search vsftpd

<p alig="center">
  <img width="1046" height="685" alt="image" src="https://github.com/user-attachments/assets/ea1aac17-4bdf-41d2-9096-b17e19824fc1" />
</p>


## 3. Used the `exploit/unix/ftp/vsftpd_234_backdoor` as exploit.
<p alig="center">
  <img width="607" height="91" alt="image" src="https://github.com/user-attachments/assets/953ca857-8e96-45e4-b1c7-1ccc226ec712" />
</p>

## 4. Use the `options` command so that we can look what to `set`.
<p alig="center">
  <img width="872" height="166" alt="image" src="https://github.com/user-attachments/assets/84fd3a7f-a232-475d-b848-57bf29231689" />
</p>











