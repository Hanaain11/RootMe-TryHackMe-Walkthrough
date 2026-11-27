# TryHackMe RootMe – Vulnerable Machine Walkthrough

## 1. Introduction

This project documents my practical experience completing the TryHackMe RootMe vulnerable machine challenge.

The objective is to identify open ports, enumerate web directories, investigate the file upload functionality and examine potential security weaknesses.

**Platform:** TryHackMe  
**Target:** RootMe  
**Operating System:** Linux (Ubuntu)

## 2. Reconnaissance – Nmap Scanning

Nmap was used to identify open ports, running services and service versions.

**Command:**
```bash
nmap -sC -sV TARGET_IP
```

**Results:**

| Port | Service | Version |
|---|---|---|
| 22 | SSH | OpenSSH 8.2p1 |
| 80 | HTTP | Apache 2.4.41 |

Two open ports were discovered: SSH (22) and HTTP (80).

## 3. Enumeration – Gobuster

Gobuster was used to discover directories and files on the target web server.

**Command:**
```bash
gobuster dir -u http://TARGET_IP -w /usr/share/wordlists/dirb/common.txt
```

**Discovered paths:**

- /css
- /js
- /panel
- /uploads
- /index.php

The `/panel/` directory contained a file upload form.

## 4. File Upload Investigation

The upload form was accessed through:

`http://TARGET_IP/panel/`

A test file named `test.txt` was uploaded successfully.

The application displayed the following message:

"O arquivo foi upado com sucesso! Veja!"

The uploaded file was then accessed through the `/uploads/` directory, confirming that the file was stored and accessible.

## 5. Evidence and Screenshots

Screenshots collected during the practical:

- Nmap scan results
- Target website
- Gobuster enumeration results
- Upload directory listing
- Successful file upload
- Uploaded test file content

## 6. Conclusion

The practical demonstrated basic network reconnaissance, web directory enumeration and file upload testing.

Further investigation is required to complete the initial access and Linux privilege escalation stages.

## 7. Flags

- User flag: Successfully obtained
- Root flag: Successfully obtained

## 8. Tools Used

- TryHackMe
- Nmap
- Gobuster
- Firefox
- Linux Terminal
