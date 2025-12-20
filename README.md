# Secure Web Application Deployment Using WAF

## Overview
This project demonstrates Secure Software Design by protecting a vulnerable web application using a Web Application Firewall (WAF).

Apache with ModSecurity and OWASP Core Rule Set (CRS) is used to detect and block common web application attacks without modifying the application source code.

---

## Architecture
Ubuntu (Attacker) → Apache + ModSecurity (WAF) → DVWA (Docker on Kali)

All HTTP requests are inspected by the WAF before reaching the application.

---

## Technologies Used
- Kali Linux
- Ubuntu Linux
- DVWA
- Docker
- Apache Web Server
- ModSecurity
- OWASP Core Rule Set (CRS)
- VirtualBox

---

## Attacks Demonstrated
- SQL Injection
- Cross-Site Scripting (XSS)
- Command Injection
- File Inclusion

---

## Security Features
- Real-time attack detection and blocking
- Anomaly-based inspection using OWASP CRS
- Secure reverse proxy deployment
- Audit logging for attack analysis

---

## How to Run
1. Start Kali and Ubuntu virtual machines
2. Start Docker and Apache services on Kali
3. Access the application via:
   http://KALI-IP:8081
4. Perform attacks from Ubuntu

---

## Disclaimer
This project is for educational purposes only and was implemented in a controlled laboratory environment.
