# Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab
A hands-on VAPT project targeting Metasploitable 2, demonstrating full attack chain from Nmap scanning to Metasploit exploitation, post-exploitation, and security remediation.

## 📊 Vulnerability & Exploitation Summary

| # | Service | Vulnerability | Access Gained | Writeup |
|---|--------|--------------|---------------|---------|
| 1 | FTP | vsFTPd 2.3.4 Backdoor | Remote Shell | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/ftp.md) |
| 2 | SSH | Weak Credentials (Brute Force via ssh_login) | SSH Access | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/ssh.md) |
| 3 | Telnet | Weak Credentials (Brute Force via telnet_login) | Telnet Access | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/telnet.md) |
| 4 | SMTP | User Enumeration via VRFY | User Discovery | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/smtp.md) |
| 5 | HTTP | PHP CGI Argument Injection (CVE-2012-1823) | Remote Code Execution (Meterpreter Shell) | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/http.md) |
