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
 > **<font color=red>serachsploit -x</font> 4401**
 > Affiche l’exploit 4401.

# Web Vulnerability Scan

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

# Graphical Interface Scanners

---

* Nessus
* GVM (ex OpenVAS)
