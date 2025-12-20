# Project Activation Guide

## Steps to Activate After Shutdown

1. Start Kali and Ubuntu virtual machines
2. Ensure Host-Only and NAT adapters are active
3. Start Docker service:
   sudo systemctl start docker
4. Start DVWA container:
   docker start $(docker ps -aq)
5. Start Apache service:
   sudo systemctl start apache2
6. Access the application via:
   http://KALI-IP:8081

## Log Monitoring
Attack logs can be viewed at:
`/var/log/apache2/modsec_audit.log`
