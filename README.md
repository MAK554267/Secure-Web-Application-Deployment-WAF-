# 🛡️ Secure Web Application Deployment Using WAF  
> **Advanced Secure Software Design for Real-Time Web Attack Detection & Prevention**

<div align="center">

![Linux](https://img.shields.io/badge/Platform-Linux-lightgrey.svg)
![Apache](https://img.shields.io/badge/Web_Server-Apache-red.svg)
![Docker](https://img.shields.io/badge/Container-Docker-blue.svg)
![ModSecurity](https://img.shields.io/badge/WAF-ModSecurity-green.svg)
![OWASP](https://img.shields.io/badge/Security-OWASP_CRS-orange.svg)
![SSD](https://img.shields.io/badge/Domain-Secure_Software_Design-purple.svg)
![Educational](https://img.shields.io/badge/Purpose-Educational-brightgreen.svg)

*A comprehensive Secure Software Design project demonstrating real-time web application attack detection and prevention using industry-standard Web Application Firewall architecture.*

</div>

---

## 🎯 Project Overview

This project demonstrates **Secure Software Design principles** by protecting a vulnerable web application against **application-layer attacks** using a **Web Application Firewall (WAF)**.

Instead of modifying the application source code, a **secure deployment architecture** is designed using **Apache + ModSecurity + OWASP Core Rule Set (CRS)** to provide **defense-in-depth**, which is widely adopted in real-world enterprise systems.

---

## 🚀 Key Features

- 🔍 Real-time attack detection  
- 🚫 Automatic blocking of malicious requests  
- 🧱 Defense-in-depth secure architecture  
- 📜 Detailed audit logging  
- ⚙️ Anomaly-based detection (OWASP CRS)  
- 🐳 Containerized application deployment  
- 🔄 Reverse proxy security layer  
- 🔐 Secure deployment without code modification  

---

## 🏗️ Secure System Architecture

Ubuntu (Attacker)
↓
Apache Web Server
+-----------------------------+
| ModSecurity (WAF) |
| + OWASP Core Rule Set |
+-----------------------------+
↓
DVWA Web Application
(Running in Docker on Kali)

yaml
Copy code

### Architecture Explanation
- All HTTP requests pass through the **WAF**
- Malicious traffic is **blocked immediately**
- Only safe requests reach the application
- All attacks are logged for monitoring

---

## 💻 Technology Stack

| Component | Technology |
|---------|------------|
| Operating System | Kali Linux |
| Attacker Machine | Ubuntu Linux |
| Web Application | DVWA |
| Containerization | Docker |
| Web Server | Apache |
| Web Application Firewall | ModSecurity |
| Security Rules | OWASP Core Rule Set |
| Virtualization | VirtualBox |

---

## 🧪 Attacks Demonstrated

- 🔴 SQL Injection  
- 🔴 Cross-Site Scripting (XSS)  
- 🔴 Command Injection  
- 🔴 File Inclusion / Directory Traversal  

All attacks were performed in a **controlled laboratory environment**.

---

## 🔐 Secure Software Design Concepts Applied

- Secure Architecture Design  
- Defense in Depth  
- Threat Modeling  
- Secure Deployment  
- Attack Surface Reduction  
- Compensating Security Controls  
- Secure Configuration Management  
- Logging and Monitoring  

---

## ⚙️ How the System Works

1. Attacker sends HTTP request  
2. Apache intercepts the request  
3. ModSecurity inspects request payload  
4. OWASP CRS evaluates anomaly score  
5. Malicious request is blocked (403 Forbidden)  
6. Attack details are logged  

---

## 📊 Logging & Monitoring

All detected attacks are logged in:

/var/log/apache2/modsec_audit.log

yaml
Copy code

Log details include:
- Attacker IP address  
- Attack type  
- Rule ID  
- Action taken  

---

## 🚀 How to Run the Project

1. Start Kali and Ubuntu virtual machines  
2. Enable Host-Only and NAT adapters  
3. Start Docker and Apache on Kali  
4. Access the secured application:

http://KALI-IP:8081

pgsql
Copy code

5. Perform attacks from Ubuntu machine  

---

## 🔄 Project Reactivation (After Shutdown)

```bash
sudo systemctl start docker apache2
docker start $(docker ps -aq)
🎓 Educational Value & Learning Outcomes
Understanding of web application vulnerabilities

Hands-on experience with Web Application Firewalls

Application of Secure Software Design principles

Real-time attack detection and mitigation

Secure deployment without source code changes

⚠️ Ethical Disclaimer
This project is intended strictly for educational purposes.
All attacks were performed on intentionally vulnerable applications in an isolated lab environment.

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

</div> ```
