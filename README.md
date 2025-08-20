# Hackademic RTB1 - CTF Walkthrough

## Target

- **Box:** Hackademic RTB1 (Realistic Hackademic Challenge)
- **Goal:** Gain root and capture the flag (`key.txt`)

## Tools Used

- `netdiscover`
- `nmap`
- `sqlmap`
- Web browser
- WordPress reverse shell
- `nc` (netcat)
- `wget`, `python3 -m http.server`
- `gcc`
- Privilege escalation exploit (EDB-ID: 15285)

## Steps Overview

1. **Network Discovery:** Find target IP using `netdiscover`.
2. **OSINT/Enumeration:** Run `nmap` for open ports and service versions.
3. **Web Recon:** Browse the site to gather info.
4. **SQL Injection:** Dump WordPress database with `sqlmap`.
5. **Credentials Extraction:** Crack admin credentials from dump.
6. **Admin Panel Access:** Log in to WordPress as admin.
7. **Web Shell Upload:** Upload PHP reverse shell via plugin editor.
8. **Reverse Shell Trigger:** Get shell as `apache`.
9. **Netcat Listener:** Set up `nc` to catch the shell.
10. **Kernel Exploit:** Use EDB-15285 for privilege escalation.
11. **File Transfer:** Host exploit via Python HTTP, transfer to box with `wget`.
12. **Compile Exploit:** Use `gcc` to compile the exploit.
13. **Root Shell:** Run exploit to gain root.
14. **Capture the Flag:** Read `key.txt` from `/root`.

## Results

- Successfully obtained root access.
- Captured the flag in `/root/key.txt`.

See walkthrough below for detailed step-by-step instructions and screenshots!
