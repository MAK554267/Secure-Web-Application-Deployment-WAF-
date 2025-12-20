🛡️ Secure Web Application Deployment Using WAF

Advanced Secure Software Design for Real-Time Web Attack Detection & Prevention

<div align="center">














A comprehensive Secure Software Design project demonstrating real-time web application attack detection and prevention using industry-standard Web Application Firewall architecture.

</div>
🎯 Project Overview

This project demonstrates Secure Software Design principles by protecting a vulnerable web application against application-layer attacks using a Web Application Firewall (WAF).

Instead of modifying the application source code, a secure deployment architecture is designed using Apache + ModSecurity + OWASP Core Rule Set (CRS) to provide defense-in-depth, which is widely adopted in real-world enterprise systems.

🚀 Key Features

🔍 Real-Time Attack Detection

🚫 Automatic Blocking of Malicious Requests

🧱 Defense-in-Depth Secure Architecture

📜 Detailed Audit Logging

⚙️ Anomaly-Based Detection (OWASP CRS)

🐳 Containerized Application Deployment

🔄 Reverse Proxy Security Layer

🔐 Secure Software Deployment Without Code Changes

🏗️ Secure System Architecture
Ubuntu (Attacker)
        ↓
Apache Web Server
+-----------------------------+
|  ModSecurity (WAF)          |
|  + OWASP Core Rule Set      |
+-----------------------------+
        ↓
DVWA Web Application
(Running in Docker on Kali)

Architecture Explanation

All HTTP requests first pass through the WAF

Malicious requests are blocked immediately

Only safe traffic is forwarded to the application

Attacks are logged for monitoring and auditing

💻 Technology Stack
Component	Technology
Operating System	Kali Linux
Attacker Machine	Ubuntu Linux
Web Application	DVWA
Containerization	Docker
Web Server	Apache
Web Application Firewall	ModSecurity
Security Rules	OWASP Core Rule Set
Virtualization	VirtualBox
🧪 Attacks Demonstrated

This project demonstrates detection and blocking of the following web application attacks:

🔴 SQL Injection

🔴 Cross-Site Scripting (XSS)

🔴 Command Injection

🔴 File Inclusion / Directory Traversal

All attacks are executed in a controlled laboratory environment.

🔐 Secure Software Design Concepts Applied

Secure Architecture Design

Defense in Depth

Threat Modeling

Secure Deployment

Attack Surface Reduction

Compensating Security Controls

Secure Configuration Management

Logging and Monitoring

This makes the project fully aligned with Secure Software Design (SSD).

⚙️ How the System Works

Attacker sends malicious HTTP request

Apache intercepts the request

ModSecurity analyzes request payload

OWASP CRS evaluates anomaly score

Malicious request is blocked (403 Forbidden)

Attack details are logged

📊 Logging & Monitoring

All detected and blocked attacks are logged in:

/var/log/apache2/modsec_audit.log


Logs include:

Attacker IP address

Attack type

Rule ID

Action taken (blocked)

🚀 How to Run the Project

Start Kali and Ubuntu virtual machines

Ensure Host-Only and NAT adapters are enabled

Start Docker and Apache services on Kali

Access the protected application:

http://KALI-IP:8081


Perform attacks from Ubuntu machine

🔄 Project Reactivation (After Shutdown)
sudo systemctl start docker apache2
docker start $(docker ps -aq)

🎓 Educational Value & Learning Outcomes

Practical understanding of web application vulnerabilities

Hands-on experience with WAF deployment

Application of Secure Software Design principles

Real-world attack simulation and mitigation

Secure deployment without modifying application code

⚠️ Ethical Disclaimer

This project is intended strictly for educational and academic purposes.
All attacks were performed in an isolated lab environment on intentionally vulnerable software.

Unauthorized testing on real systems is illegal and unethical.

📚 References

OWASP Top 10 Web Application Security Risks

OWASP ModSecurity Core Rule Set

Apache HTTP Server Documentation

Docker Documentation

NIST Secure Software Development Framework (SSDF)

<div align="center">

🎓 Developed for Secure Software Design (SSD)
University of Wah – BS Cybersecurity








⭐ Star this repository if it helped your Secure Software Design learning journey!

</div>
