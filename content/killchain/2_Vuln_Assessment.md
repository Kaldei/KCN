---
title: 2 – Vulns Assessment
summary: Vulnerability Assessment step – a note for finding and assessing vulnerabilities.
description: Vulnerability Assesment step – a note for finding and assessing vulnerabilities.
---

# Exploit Database

---

### SEARCHSPLOIT


 > 
 > **<font color=orange>apt install exploitdb</font>**
 > 
 > **<font color=red>serachsploit</font> name version**
 > Recherche d’exploits connues (de Exploit-DB).
 > 
 > **<font color=red>serachsploit -x</font> 4401**
 > Affiche l’exploit 4401.

# Web Vulnerability Scanners

---

### NICKTO


 > 
 > **<font color=red>nikto -h</font> \[TARGET_IP\]**	
 > Web vuln scan.
 > 
 > **<font color=red>nikto -h http://</font>\[TARGET_IP\]:\[TARGET_PORT\]<font color=red>/</font>path <font color=red>-id</font> myUser<font color=red>:</font>myPass**
 > Web vuln scan with credential and login page.

---

### WPSCAN


 > 
 > **<font color=red>wpscan --url</font> \[TARGET_IP\] <font color=red>-e u,vp,vt</font>**  
 > Scan Wordpress.


 > 
 > **<font color=red>-e vp</font>**
 > Enumerate Vulnerable Plugins.
 > 
 > **<font color=red>-e vt</font>**
 > Enumerate Vulnerable Themes.
 > 
 > **<font color=red>-e cb</font>**
 > Enumerate Config Backups.
 > 
 > **<font color=red>-e dbe</font>**
 > Enumerate DB Exports.
 > 
 > **<font color=red>-e u</font>**
 > Enumerate Users.

# General Vulnerability Scanners

---

### NESSUS

**[https://docs.tenable.com/nessus/Content/DeployNessusDocker.htm](https://docs.tenable.com/nessus/Content/DeployNessusDocker.htm)** 

 > 
 > **<font color=red>docker run -p 8834:8834 --name nessus tenableofficial/nessus</font>**</br>
 > Start Nessus scanner.

The scanner will be accessible at: [https://127.0.0.1:8834/](https://127.0.0.1:8834/)

To use the scanner, you need to create an account.</br>
You can create a free Nessus Essentials account here: [https://fr.tenable.com/products/nessus/nessus-essentials](https://fr.tenable.com/products/nessus/nessus-essentials)

---

### Greenbone Vulnerability Manager

**[https://greenbone.github.io/docs/latest/22.4/container/index.html](https://greenbone.github.io/docs/latest/22.4/container/index.html)**

 > 
 > **<font color=red>curl -f -L https://greenbone.github.io/docs/latest/\_static/docker-compose-22.4.yml -o docker-compose.yml</font>**</br>
 > Download Docker Copose file.
 > 
 > **<font color=red>docker-compose -f docker-compose.yml -p greenbone-community-edition up</font>**</br>
 > Start Greenbone scanner.
 > 
 > **<font color=red>docker-compose -f docker-compose.yml -p greenbone-community-edition down</font>**</br>
 > Stop Greenbone scanner.

The scanner will be accessible with default credentials (admin:admin) at: [http://127.0.0.1:9392/](http://127.0.0.1:9392/)
