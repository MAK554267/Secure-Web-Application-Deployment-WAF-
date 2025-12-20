# Secure-Web-App-Deployment-WAF-
# Secure Web Application Deployment Using WAF

## Project Overview
This project demonstrates Secure Software Design by protecting a vulnerable web application using a Web Application Firewall (WAF).

The system uses Apache with ModSecurity and OWASP Core Rule Set (CRS) to detect and block common web application attacks such as SQL Injection, Cross-Site Scripting (XSS), Command Injection, and File Inclusion.

---

## Project Objectives
- Design a secure deployment architecture for a web application
- Protect the application without modifying its source code
- Detect and block common web-based attacks
- Maintain logs for security monitoring and auditing

---

## System Architecture
Ubuntu (Attacker) → Apache + ModSecurity (WAF) → DVWA (Docker)

All incoming HTTP requests are inspected by the WAF before reaching the application.

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
- Real-time detection and blocking
- Anomaly-based attack detection
- Audit logging
- Secure reverse proxy deployment

---

## Repository Structure
- `documentation/` – Proposal and report
- `architecture/` – System architecture diagram
- `configuration/` – WAF and proxy configuration files
- `attacks/` – Test payloads used for attack simulation
- `screenshots/` – Proof of attack detection and blocking
- `activation_guide.md` – Steps to restart the project

---

## Disclaimer
This project is intended for educational purposes only and was implemented in a controlled laboratory environment.
