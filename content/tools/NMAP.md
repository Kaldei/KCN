---
title: NMAP
---

## NMAP Base


 > 
 > **<font color=red>nmap -sn</font> \[TARGET_NETWORK\]/24</br>**
 > Do not do port scan: scan for hosts (ARP, ICMP, TCP/UDP Ping). 

 > 
 > **<font color=red>nmap -sV -sC</font>  \[TARGET_IP\]</br>**
 > Ports services + Default script.

## NMAP Host dicovering Process (-sn)

* **Privileged user scans targets in local network:**  ARP requests.
* **Privileged user scans targets outside local network:** ICMP echo requests, TCP ACK to port 80, TCP SYN to port 443, and ICMP timestamp request.
* **Unprivileged user scans targets outside local network:** SYN to ports 80 and 443.

## NMAP Flags


 > 
 > **<font color=red>-O</font></br>**
 > OS detection.
 > 
 > **<font color=red>-sV</font></br>**
 > Service detection (Force Nmap to proceed with the TCP 3-way handshake).
 > 
 > **<font color=red>-oN</font> myOutputFile</br>**
 > Normal Output.

 > 
 > **<font color=red>-vv</font></br>**
 > Verbose.
 > 
 > **<font color=red>-n</font></br>**
 > Do not resolve DNS.
 > 
 > **<font color=red>-Pn</font></br>**
 > Do not ping to determine if host is up.
 > 
 > **<font color=red>-r</font></br>**
 > Scan the ports in consecutive order instead of random order.

## NMAP Ports


 > 
 > **<font color=red>-p </font>80</br>**
 > Scan port 80.
 > 
 > **<font color=red>-p</font> 80<font color=red>,</font>443</br>**
 > Scan ports 80 and 443.
 > 
 > **<font color=red>-p</font> 80<font color=red>-</font>443</br>**
 > Scan ports 80 to 443. 
 > 
 > **<font color=red>-p-</font></br>**
 > Scan all ports.

## NMAP Timing


 > 
 > **<font color=red>-T0</font></br>**
 > Paranoid (5 minutes between sending each probe/ Avoid IDS Dectection).
 > 
 > **<font color=red>-T1</font></br>**
 > Sneaky (Avoid IDS Dectection).
 > 
 > **<font color=red>-T2</font></br>**
 > Polite.
 > 
 > **<font color=red>-T3</font></br>**
 > Normal (Default).
 > 
 > **<font color=red>-T4</font></br>**
 > Aggressive.
 > 
 > **<font color=red>-T5</font></br>**
 > Insane (Can affect scan accuracy)

## NMAP Scans Types


 > 
 > **<font color=red>-sT</font></br>**
 > TCP connect scan. Default running with non privileged users.
 > 
 > **<font color=red>-sS</font></br>**
 > SYN scan (Half TCP / “Sneaky”). Default running with privileged users.
 > 
 > **<font color=red>-sU</font></br>**
 > UDP port scan.

## NMAP Firewall Bypass and Evasion


 > 
 > **<font color=red>-sN</font></br>**
 > Null scan (do not set any TCP flag). No response is either port open or filtered.
 > 
 > **<font color=red>-sF</font></br>**
 > FIN scan (FIN flag). No response is either port open or filtered.
 > 
 > **<font color=red>-sX</font></br>**
 > Xmas scan (FIN, PSH, and URG flags simultaneously). No response is either port open or filtered.
 > 
 > **<font color=red>-A</font></br>**
 > Used to discover firewall rules. Return unfiltered ports (dosn't mean they're up).
 > 
 > **<font color=red>-D</font> \[TARGET_IP\]RND,ME</br>**
 > Send same request with decoy IP addresses (RND is Random IP and ME is my IP).
 > 
 > **<font color=red>-f </font>and <font color=red>-ff</font></br>**
 > Send fragmented packets (divided into 8 and 16 bytes).

## NMAP Scripts

[https://nmap.org/nsedoc/](https://nmap.org/nsedoc/) 

**<font color='lightblue'>/usr/share/nmap/scripts</font>**

![](https://lh5.googleusercontent.com/NHTCdufcZiTMmjJMx6MED47ZsVmNnTlLSwDAY7PkxCSbzdz88uaTSKEpHTILX5QhDs-tza6hgufWPm8u5Iy1enfl_wpXfF2XTzUBSRF6Z4g_31kxlbrqSIxqSN7tZZh89Tflpkj_OmjrGXgPCA)

 > 
 > **<font color=red>-sC</font></br>**
 > Default script scanning.
 > 
 > **<font color=red>-A</font></br>**
 > Agressive Scan (-O + -sV + -sC + --traceroute).

 > 
 > **<font color='red'>--script</font> vuln</br>**
 > Run a script.	
 > 
 > **<font color='red'>--script</font> http-put <font color='red'>--script-args</font></br>**
 > http-put.url='/dav/shell.php',http-put.file='./shell.php' : Script with arguments

## NMAP SMB Scan


 > 
 > **<font color=red>nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse</font> \[TARGET_IP\]</br>**
 > Search for SMB Shares.

 > 
 > **<font color=red>nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount</font> \[TARGET_IP\]</br>**
 > Enumerate rpcbind.
