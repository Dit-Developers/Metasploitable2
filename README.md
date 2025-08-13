# 🔍 Vulnerability Assessment on Metasploitable2 using Nmap and Nessus

## 📌 Overview

This project demonstrates a vulnerability assessment on **Metasploitable2**, a deliberately vulnerable Linux machine, using a combination of **Nmap**, **Nessus Essentials**, and manual CVE research. The goal was to identify open ports, detect service versions, and uncover known security vulnerabilities that could potentially be exploited by attackers. The assessment includes both manual enumeration techniques and automated vulnerability scanning for comprehensive coverage.


## 🛠 Tools Used

- **Nmap** – Port scanning, service/version detection, and NSE vulnerability scripts
- **Nessus Essentials** – Vulnerability scanner used to detect critical and high-risk issues with CVE references and remediation guidance.
- **Kali Linux** – Attacker machine
- **Metasploitable2** – Vulnerable target machine (metaspolitable2 ip)
- **Manual CVE Analysis** – Researched vulnerabilities based on Nmap findings


## 📶 Lab Setup

| Component         | IP Address     |
|------------------|----------------|
| Attacker Machine | kali linux  |
| Target Machine   | metasploitable2  |

- Network: Host-Only Adapter (isolated environment)


## 🧪1: Nmap Scan - Steps Performed

1. **Basic Port Scan**  
   Identified open ports using `nmap <target-ip>`

2. **Service & Version Detection**  
   Detected versions of running services:  
   `nmap -sV <target-ip>`

3. **Aggressive Scan with OS Detection**  
   `nmap -A <target-ip>`

4. **Vulnerability Script Scan**  
   Used built-in Nmap NSE scripts:  
   `nmap --script vuln <target-ip>`

5. **Manual CVE Lookup**  
   Based on Nmap output, identified known vulnerabilities with CVEs


## 📝 Key Vulnerabilities Found

| Port | Service    | Version        | Vulnerability                        | CVE ID         | Risk  | Mitigation Suggestion                          |
|------|------------|----------------|--------------------------------------|----------------|-------|------------------------------------------------|
| 21   | vsftpd     | 2.3.4          | Backdoor command execution           | CVE-2011-2523  | High  | Disable vsftpd or upgrade to secure version   |
| 443  | OpenSSL    | TLS/SSL        | Weak Diffie-Hellman key exchange     | CVE-2015-4000  | High  | Use strong ciphers, disable weak DH suites    |
| 443  | SSL/TLS    | SSLv3 Enabled  | SSLv3 vulnerability (POODLE attack)  | CVE-2014-3566  | Medium| Disable SSLv3, enforce TLS 1.2 or higher       |

---

## 📸 Screenshots

![p1](https://github.com/user-attachments/assets/28bd35d5-ef6b-4c16-b293-f62c0b37b163)
![p2](https://github.com/user-attachments/assets/71f186d5-80ce-44c3-9e1e-723cf8f4fae9)
![p3](https://github.com/user-attachments/assets/714d245a-fa23-48d4-a288-78978c24fa2d)
![p4](https://github.com/user-attachments/assets/6710c0f6-c4ee-4133-8d15-8aff96ea65fd)
![p5](https://github.com/user-attachments/assets/57be62f6-3ed4-4179-8eb0-97e847d87d82)




## 🛡 Mitigation Summary

- Disable insecure services like FTP and Telnet
- Apply security patches to known vulnerable services
- Upgrade legacy software to supported, secure versions
- Enforce strong encryption and modern SSL/TLS protocols


---

## 2. 🧪 Nessus Vulnerability Scan 

To strengthen the assessment, a Nessus scan was also performed on the Metasploitable2 machine. This helped in identifying additional high-risk vulnerabilities with detailed CVE information and mitigation suggestions.

### 🔍 Nessus Scan Summary

- Scan Type: Advanced Network Scan
- Target: metasplotable2 ip
- Total Vulnerabilities Detected: 65
  - Critical: 11
  - High: 15
  - Medium: 39
  - 
- Detected **65 vulnerabilities**
- Identified multiple backdoors, outdated software, and misconfigurations
- Target OS: **Linux Kernel*

  
### 📸 Nessus Screenshot
![p6](https://github.com/user-attachments/assets/03a1819f-719e-49d9-be32-f4a872ac010e)
