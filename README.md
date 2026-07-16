# VulnScan Lab — Penetration Testing Portfolio

Personal home lab built on VirtualBox. Each folder documents a complete
pentest cycle — recon, exploitation, post-exploitation, and a professional PDF report.

**Lab Setup**
- Attacker : Kali Linux — 192.168.1.11
- Targets  : Metasploitable 2, Windows 7 SP1 VM, Windows Server
- Network  : Bridged LAN (isolated home network)
- Tools    : Nmap, Metasploit Framework, Wireshark, Burp Suite

---

## Completed

| # | Vulnerability | CVE | Severity | Target | Access | Report |
|---|---|---|---|---|---|---|
| 1 | vsftpd 2.3.4 Backdoor | CVE-2011-2523 | 🔴 Critical | Metasploitable 2 | root | [View](./01-vsftpd-backdoor/report.pdf) |
| 2 | Samba usermap_script | CVE-2007-2447 | 🔴 Critical | Metasploitable 2 | root | [View](./02-samba-usermap/report.pdf) |
| 3 | EternalBlue MS17-010 | CVE-2017-0144 | 🔴 Critical | Windows 7 SP1 | NT AUTHORITY\SYSTEM | [View](./03-eternalblue-ms17010/report.pdf) |

---

### 01 — vsftpd 2.3.4 Backdoor (CVE-2011-2523)

**Service:** FTP — Port 21 &nbsp;|&nbsp; **Access:** root via Meterpreter

vsftpd 2.3.4 contained a malicious backdoor introduced into the source tarball.
Sending a username containing `:)` opens a root shell on port 6200.

![vsftpd host discovery](./01-vsftpd-backdoor/screenshots/01_host_discovery.png)
![vsftpd root confirmed](./01-vsftpd-backdoor/screenshots/04_root_confirmed.png)

[→ Full writeup](./01-vsftpd-backdoor/)

---

### 02 — Samba usermap_script (CVE-2007-2447)

**Service:** SMB — Ports 139/445 &nbsp;|&nbsp; **Access:** root via reverse shell

Samba 3.0.20 passes username input unsanitized to a shell. Injecting shell
metacharacters during MS-RPC authentication triggers unauthenticated RCE as root.

![samba nmap](./02-samba-usermap/screenshots/01_nmap_samba.png)
![samba root](./02-samba-usermap/screenshots/04_root_confirmed.png)

[→ Full writeup](./02-samba-usermap/)

---

### 03 — EternalBlue MS17-010 (CVE-2017-0144)

**Service:** SMB — Port 445 &nbsp;|&nbsp; **Access:** NT AUTHORITY\SYSTEM + hashdump

NSA-developed exploit targeting Windows SMBv1. Buffer overflow in Trans2 request
handling delivers a Meterpreter shell as SYSTEM with no authentication.
All 4 Windows account NTLM hashes retrieved via hashdump.

![eternalblue nmap](./03-eternalblue-ms17010/screenshots/01_nmap_scan.png)
![eternalblue system](./03-eternalblue-ms17010/screenshots/03_exploit_root_hashdump.png)

[→ Full writeup](./03-eternalblue-ms17010/)

---

## In Progress

| # | Vulnerability | Target | Status |
|---|---|---|---|
| 4 | DVWA SQL Injection | Metasploitable 2 | 🔄 Next |

---

## Skills Demonstrated

- Network reconnaissance — Nmap (`-sV`, `-sC`, `-oN`, NSE scripts)
- Vulnerability identification and CVE mapping
- Metasploit Framework — module selection, payload configuration, session handling
- Linux exploitation — FTP backdoor, SMB command injection
- Windows exploitation — SMBv1 kernel overflow, SYSTEM-level access
- Credential harvesting — Windows SAM hashdump, NTLM hash analysis
- Post-exploitation enumeration across Linux and Windows targets
- Structured professional penetration test report writing