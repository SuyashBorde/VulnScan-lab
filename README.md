# VulnScan Lab — Penetration Testing Portfolio

Personal home lab built on VirtualBox. Each folder documents a complete
pentest cycle — recon, exploitation, post-exploitation, and a professional PDF report.

**Lab Setup**
- Attacker : Kali Linux — 192.168.1.10
- Targets  : Metasploitable 2, Windows VM, Windows Server
- Network  : Bridged LAN (isolated home network)
- Tools    : Nmap, Metasploit Framework, Wireshark, Burp Suite

---

## Completed

| # | Vulnerability | CVE | Severity | Target | Report |
|---|---|---|---|---|---|
| 1 | vsftpd 2.3.4 Backdoor | CVE-2011-2523 | 🔴 Critical | Metasploitable 2 | [View](./01-vsftpd-backdoor/report.pdf) |
| 2 | Samba usermap_script | CVE-2007-2447 | 🔴 Critical | Metasploitable 2 | [View](./02-samba-usermap/report.pdf) |

---

### 01 — vsftpd 2.3.4 Backdoor (CVE-2011-2523)

**Service:** FTP — Port 21 &nbsp;|&nbsp; **Access:** Root Meterpreter shell

vsftpd 2.3.4 was distributed with a malicious backdoor. Sending a username
containing `:)` opens a root shell on port 6200. Exploited via Metasploit
to gain a Meterpreter session with `uid=0(root)`.

![vsftpd host discovery](./01-vsftpd-backdoor/screenshots/01_host_discovery.png)
![vsftpd root confirmed](./01-vsftpd-backdoor/screenshots/04_root_confirmed.png)

[→ Full writeup](./01-vsftpd-backdoor/)

---

### 02 — Samba usermap_script (CVE-2007-2447)

**Service:** SMB — Ports 139/445 &nbsp;|&nbsp; **Access:** Root command shell

Samba 3.0.20 passes username input unsanitized to a shell script. Injecting
shell metacharacters during MS-RPC authentication triggers remote command
execution as root. Exploited via `exploit/multi/samba/usermap_script`.

![samba nmap](./02-samba-usermap/screenshots/01_nmap_samba.png)
![samba root](./02-samba-usermap/screenshots/04_root_confirmed.png)

[→ Full writeup](./02-samba-usermap/)

---

## In Progress

| # | Vulnerability | CVE | Target | Status |
|---|---|---|---|---|
| 3 | EternalBlue / MS17-010 | CVE-2017-0144 | Windows VM | 🔄 Next |
| 4 | DVWA SQL Injection | OWASP A03 | Metasploitable 2 | Planned |

---

## Skills Demonstrated

- Network reconnaissance with Nmap (`-sV`, `-sC`, `-oN`)
- Vulnerability identification and CVE mapping
- Metasploit Framework — module selection, payload configuration, session handling
- Post-exploitation enumeration (uid, hostname, kernel version)
- Structured penetration test report writing
- Home lab setup — VirtualBox, Kali Linux, Metasploitable 2