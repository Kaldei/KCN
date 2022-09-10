---
title: 1 - Enumeration
---

# Host Dicovering

---

### ARP Scan


 > 
 > **<font color=red>arp -scan -l -I</font> eth0**</br>
 > Scan for hosts in the same network of the specifeid interface.

 > 
 > **<font color=red>netdiscover -r</font> \[TARGET_NETWORK\]/24**</br>
 > Return MAC address of this network.

---

### MASSCAN


 > 
 > **<font color=red>masscan</font> \[TARGET_NETWORK\]/24 <font color=red>-p</font>443</br>**
 > Host discovering scan.

# Port Scan

---

### NMAP


 > 
 > **<font color=red>nmap -sn</font> \[TARGET_NETWORK\]/24</br>**
 > Do not do port scan: scan for hosts (ARP, ICMP, TCP/UDP Ping). 

 > 
 > **<font color=red>nmap -sV -sC</font>  \[TARGET_IP\]</br>**
 > Ports services + Default script.

# SMB Scan

---

### SMBCLIENT


 > 
 > **<font color=red>smbclient -L </font>\[TARGET_IP\]<font color=red> --no-pass</font></br>**
 > List Shares anonymously.

 > 
 > **<font color=red>smbclient -L </font>\[TARGET_IP\]<font color=red> -U</font> myUser</br>**
 > List Shares with a user.

 > 
 > **<font color=red>smbclient</font> <font color=red>//</font>\[TARGET_IP\]<font color=red>/</font>mySmbShare</br>**
 > Connect to a Share.

---

### NMAP


 > 
 > **<font color=red>nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse</font> \[TARGET_IP\]</br>**
 > Search for SMB Shares.

 > 
 > **<font color=red>nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount</font> \[TARGET_IP\]</br>**
 > Enumerate rpcbind.

---

### ENUM4LINUUX


 > 
 > **<font color=red>enum4linux -S</font> \[TARGET_DOMAIN\]</br>**
 > List Samba Share.

# Subdomains Fuzz

---

### ASSETFINDER

[https://github.com/tomnomnom/assetfinder](https://github.com/tomnomnom/assetfinder) 

 > 
 > **<font color=orange>go install github.com/tomnomnom/assetfinder@latest</font>**
 > 
 > **<font color=red>assetfinder</font> \[TARGET_DOMAIN\]**</br>
 > Find subdomains and some that could be related.
 > 
 > **<font color=red>assetfinder --subs-only</font> \[TARGET_DOMAIN\]**</br>
 > Find only subdomains (stay in the scope).

---

### AMMAS

https://github.com/OWASP/Amass 

 > 
 > **<font color=orange>go install github.com/OWASP/Amass/v3/...@master</font>**
 > 
 > **<font color=red>amass enum -d</font> \[TARGET_DOMAIN\]**</br>
 > Find subdomains.

---

### DNSRECON


 > 
 > **<font color=red>dnsrecon -t brt -d</font> \[TARGET_DOMAIN\]**</br>
 > Find subdomains (brute force).

---

### SUBLIST3R


 > 
 > **<font color=red>sublist3r.py -d</font>  \[TARGET_DOMAIN\]</br>**
 > Find subdomains (using search engines).

# Web Paths Fuzz

---

### Word Lists

* **<font color='lightblue'>/usr/share/wordlists/drib/big.txt/</font> \<- Really Good**
* **<font color='lightblue'>/usr/share/wordlists/dirb/common.txt/</font> ← Fast**
* **<font color='lightblue'>/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt/</font>← Medium**

---

### Known Paths

* Tomcat -> /manager
* Liferay -> /admin ?
* Durpal-> /admin ou /drupal
* Typo3 -> /typo3/
* Matomo -> /administrator ?
* Joomla -> /administrator
* Kentico -> /cms -> /CMSPages/logon.aspx
* October -> /backend -> /backend/backend/auth/signin
* Umbraco -> /umbraco/ -> /umbraco/login.aspx
* Laravel -> /admin -> /admin/auth/login

---

### GOBUSTER


 > 
 > **<font color=red>gobuster dir -u</font> http://\[TARGET_IP\]:\[TARGET_PORT\] <font color=red>-w</font> myWordList <font color=red>-x</font> php,txt,html</br>**
 > Search files.
 > 
 > **<font color=red>gobuster dir -u</font> http://\[TARGET_IP\]:\[TARGET_PORT\] <font color=red>-w</font> myWordList</br>**
 > Search folders.

---

### FUFF


 > 
 > **<font color=red>fuff -w</font> /usr/share/wordlists/seclists/Discovery/Web-Content/big.txt<font color=red>:FUZZ -u</font> http://\[TARGET_DOMAIN\]/<font color=red>FUZZ</font></br>**
 > Web Path FUZZ

---

### WFUZZ


 > 
 > **<font color=red>wfuzz -c -z file,</font>myWordList http://\[TARGET_IP\]:\[TARGET_PORT\]/<font color=red>FUZZ</font></br>**
 > Fuzz Folders

# API Fuzz

---

### WFUZZ


 > 
 > **<font color=red>wfuzz -c -z file,</font>myWordList http://\[TARGET_IP\]:\[TARGET_PORT\]/api/file?parameter=<font color=red>FUZZ</font></br>**
 > Fuzz API

# Virutals Hosts Fuzz

---

### FUFF


 > 
 > **<font color=red>ffuf -w</font> <font color=lightblue>/usr/share/wordlists/seclists/Discovery/DNS/namelist.txt</font> <font color=red>-H "Host: FUZZ.</font>\[TARGET_DOMAIN\]<font color=red>" -u</font> http://\[TARGET_DOMAIN\] <font color=red>-fs</font> 2395</br>**
 > Virtual Host FUZZ

# User Fuzz

---

### FUFF


 > 
 > **<font color=red>ffuf -w</font> <font color=lightblue>/usr/share/wordlists/seclists/Usernames/Names/names.txt</font> <font color=red>-X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u</font> http://\[TARGET_DOMAIN\]/signup <font color=red>-mr </font>"username already exists"</br>**
 > User Enumeration
