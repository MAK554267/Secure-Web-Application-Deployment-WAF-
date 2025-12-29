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

This project demonstrates **Secure Software Design (SSD)** principles by protecting a vulnerable web application against **application-layer attacks** using a **Web Application Firewall (WAF)**.

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
```
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

```


### Architecture Explanation

- All HTTP requests pass through the **Web Application Firewall**
- Malicious traffic is **blocked immediately**
- Only legitimate requests reach the application
- All detected attacks are logged for monitoring and auditing

---

## 💻 Technology Stack

| Component | Technology |
|----------|------------|
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

1. Attacker sends an HTTP request  
2. Apache intercepts the request  
3. ModSecurity inspects the request payload  
4. OWASP CRS evaluates the anomaly score  
5. Malicious request is blocked (**403 Forbidden**)  
6. Attack details are logged  

---

## 📊 Logging & Monitoring

All detected attacks are logged in:
/var/log/apache2/modsec_audit.log

Log details include:
- Attacker IP address  
- Attack type  
- Triggered rule ID  
- Action taken (Blocked)  

---

## 🚀 How to Run the Project

1. Start Kali and Ubuntu virtual machines  
2. Enable **Host-Only** and **NAT** network adapters  
3. Run DVWA in Docker on Kali
   ```bash
   sudo docker run -d -p 8080:80 vulnerables/web-dvwa
   ```
   Check:
   ```bash
   sudo docker ps  
4. Install Apache + ModSecurity (KALI)
   ```bash
   sudo apt update 
   sudo apt install apache2 libapache2-mod-security2 git -y
   ```
   Enable modules:
   ```bash
   sudo a2enmod security2 
   sudo a2enmod proxy 
   sudo a2enmod proxy_http
   ```
5. Enable ModSecurity Blocking Mode
   ```bash
   sudo cp /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf 
   sudo nano /etc/modsecurity/modsecurity.conf
   ```
   Change:
   ```bash
   SecRuleEngine DetectionOnly
   ``` 
   To:
   ```bash 
   SecRuleEngine On
   ``` 
   Save & exit.
6. Install OWASP CRS
   ```bash
   cd /etc/modsecurity 
   sudo git clone https://github.com/coreruleset/coreruleset.git 
   cd coreruleset 
   sudo cp crs-setup.conf.example crs-setup.conf
   ```
7. Link CRS with Apache (IMPORTANT)
    Edit: 
    ```bash
   sudo nano /etc/apache2/mods-enabled/security2.conf
    ``` 
   Use ONLY this content:
   ```bash
    <IfModule security2_module> 
      SecDataDir /var/cache/modsecurity 
      Include /etc/modsecurity/modsecurity.conf 
      Include /etc/modsecurity/coreruleset/crs-setup.conf 
      Include /etc/modsecurity/coreruleset/rules/*.conf 
    </IfModule>
   ```
8. Fix ModSecurity Logs (IMPORTANT)
      ```bash
      sudo touch /var/log/apache2/modsec_audit.log 
      sudo chown www-data:www-data /var/log/apache2/modsec_audit.log 
      sudo chmod 640 /var/log/apache2/modsec_audit.log
      ```
9. Set Apache Reverse Proxy (WAF)

    **Change Apache Port**

    ```apache
    sudo nano /etc/apache2/ports.conf
    ```

    Add:
    ```apache
    Listen 8081
    ```

    **Create WAF Site**

    ```bash
    sudo nano /etc/apache2/sites-available/dvwa-waf.conf
    ```

    ```apache
    <VirtualHost *:8081>
        ProxyPreserveHost On
        ProxyPass / http://127.0.0.1:8080/
        ProxyPassReverse / http://127.0.0.1:8080/
    </VirtualHost>
    ```

    **Enable the Site**

    ```bash
    sudo a2ensite dvwa-waf.conf
    sudo a2dissite 000-default.conf
    ```

10. Increase Blocking Sensitivity (VERY IMPORTANT)
    ```bash
    sudo nano /etc/modsecurity/coreruleset/crs-setup.conf
    ```
    Uncomment & set:
    ```bash
    SecAction \ 
     "id:900110,phase:1,nolog,pass,t:none,\ 
      setvar:tx.inbound_anomaly_score_threshold=1"
    ```
11. Start Everything
    ```bash
    sudo apachectl configtest 
    sudo systemctl restart apache2 
    sudo systemctl status apache2 
    ```
12. Correct URLs (REMEMBER)
    |Purpose|URL|
    |--------------|-------| 
    |DVWA without WAF|http://KALI-IP:8080| 
    |DVWA protected|http://KALI-IP:8081|
13. Log Monitoring
    ```bash
    sudo tail -f /var/log/apache2/modsec_audit.log
    ```


## 🔄 Project Reactivation (After Shutdown)

```bash
sudo systemctl start docker apache2
docker start $(docker ps -aq)
```

## 🎓 Educational Value & Learning Outcomes

- Practical understanding of web application vulnerabilities  
- Hands-on experience with Web Application Firewall (WAF) deployment  
- Application of Secure Software Design (SSD) principles  
- Real-world attack simulation and mitigation  
- Secure deployment without modifying application source code  

---

## ⚠️ Ethical Disclaimer

This project is intended **strictly for educational and academic purposes**.  
All attacks were performed in an **isolated laboratory environment** on intentionally vulnerable software.

Unauthorized testing on real systems is **illegal and unethical**.

---

## 📚 References

- OWASP Top 10 Web Application Security Risks  
- OWASP ModSecurity Core Rule Set  
- Apache HTTP Server Documentation  
- Docker Documentation  
- NIST Secure Software Development Framework (SSDF)  

---

<div align="center">

**🎓 Developed for Secure Software Design (SSD)**

*Applying secure software principles through hands-on cybersecurity research*

[![University](https://img.shields.io/badge/Institution-University_of_Wah-blue.svg)](#)
[![Program](https://img.shields.io/badge/Program-BS_Cybersecurity-purple.svg)](#)
[![Course](https://img.shields.io/badge/Course-Secure_Software_Design-teal.svg)](#)
[![Semester](https://img.shields.io/badge/Semester-5th-green.svg)](#)
[![Project](https://img.shields.io/badge/Type-Academic_Project-orange.svg)](#)

---

**"Secure by design, resilient by practice."**

**⭐ Star this repository if it supported your Secure Software Design learning journey!**

</div>



