# Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab
A hands-on VAPT project targeting Metasploitable 2, demonstrating full attack chain from Nmap scanning to Metasploit exploitation, post-exploitation, and security remediation.

## 📊 Vulnerability & Exploitation Summary

| # | Service | Vulnerability | Access Gained | Writeup |
|---|--------|--------------|---------------|---------|
| 1 | FTP | vsFTPd 2.3.4 Backdoor | Remote Shell | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/ftp.md) |
| 2 | SSH | Weak Credentials (Brute Force via ssh_login) | SSH Access | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/ssh.md) |
| 3 | Telnet | Weak Credentials (Brute Force via telnet_login) | Telnet Access | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/telnet.md) |
| 4 | SMTP | User Enumeration via VRFY | User Discovery | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/smtp.md) |
| 5 | HTTP | PHP CGI Argument Injection | Remote Code Execution (Meterpreter Shell) | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/http.md) |
| 6 | NFS (111/2049) | Misconfigured NFS Export (No Root Squash) | Root Access via SSH Key Injection | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/111&2049_port.md) |
| 7 | SMB (139/445) | Samba "username map script" Command Execution | Remote Root Shell | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/139&445_port.md) |
| 8 | RSH/RLOGIN/REXEC (512/513/514) | Trust-Based Authentication (rhosts / hosts.equiv Misconfiguration) | Remote Shell Access (rsh / rlogin) | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/512_513_514_port.md) |
| 9 | ProFTPD (2121) | ProFTPD Backdoor Command Execution | Remote Shell Access | [View](https://github.com/OmDorugade/Metasploitable-2-End-to-End-Penetration-Testing-Home-Lab/blob/main/writeups/2121_port_tcp_PROFTPD.md) |
