# VulnScan Lab — Penetration Testing Portfolio

Personal home lab built on VirtualBox. Each folder contains
a full pentest cycle — recon, exploitation, post-exploitation,
and a professional PDF report.

**Lab Setup**
- Attacker : Kali Linux — 192.168.1.12
- Targets  : Metasploitable 2, Windows VM, Windows Server
- Network  : Bridged LAN (isolated home network)

---

## Completed

| # | Vulnerability | CVE | Severity | Report |
|---|---|---|---|---|
| 1 | vsftpd 2.3.4 Backdoor | CVE-2011-2523 | Critical | [View](./01-vsftpd-backdoor/vsftpd_pentest_report.pdf) |

---

### 01 — vsftpd 2.3.4 Backdoor (CVE-2011-2523)

**Target:** Metasploitable 2 — 192.168.1.14
**Tool:** Metasploit Framework
**Result:** Root shell via Meterpreter

#### Host Discovery
![Host Discovery](./01-vsftpd-backdoor/screenshots/01_host_discovery.png)

#### Metasploit Configuration
![MSF Config](./01-vsftpd-backdoor/screenshots/02_msf_config.png)

#### Session Opened
![Session Opened](./01-vsftpd-backdoor/screenshots/03_session_opened.png)

#### Root Access Confirmed
![Root Confirmed](./01-vsftpd-backdoor/screenshots/04_root_confirmed.png)

---

## In Progress

| # | Vulnerability | Target |
|---|---|---|
| 2 | Samba usermap_script | Metasploitable 2 |
| 3 | EternalBlue MS17-010 | Windows VM |
| 4 | DVWA SQL Injection | Metasploitable 2 |