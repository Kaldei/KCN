---
title: JOHN
---

## Base


 > 
 > **<font color=red>john --wordlist=</font>/usr/share/wordlists/rockyou.txt hash.txt**</br>
 > Crack unknown hash.

## Flags


 > 
 > **<font color=red>--fork=</font>4**</br>
 > Parallelization

## Linux Unshadow


 > 
 > **<font color=red>unshadow /etc/passwd /etc/shadow ></font> unshadowd.txt**</br>
 > Prepare passwd and shadow file for John.
 > 
 > **<font color=red>john unshadow.txt --wordlist=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Crack user passwords.
 > 
 > **<font color=red>john --show</font> unshadow.txt**</br> 
 > Display cracked passwords.

## SSH Private Key Passphrase


 > 
 > **<font color=red>/usr/share/john/ssh2john.py</font> private_key <font color=red>\></font> forjohn.txt**</br>
 > Prepare private key for John.
 > 
 > **<font color=red>john --wordlist=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font> forjohn.txt**</br>
 > Crack private key passphrase.

## JWT


 > 
 > **<font color=red>john --format=HMAC-SHA512</font> jwt.txt <font color=red>--show</font>**</br>
 > Crack JWT secret.

## MD5


 > 
 > **<font color=red>john --format=md5crypt --wordlist=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font> hash.txt**</br>
 > Crack MD5 hash.

## NTLM


 > 
 > **<font color=red>john --format=NT -w=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font> hash.txt <font color=red>--pot=</font>output.txt**</br>
 > Crack NTLM Hash.

## RAR


 > 
 > **<font color=red>rar2john</font> myFile.rar <font color=red>\></font> forjohn.txt**</br>
 > Prepare RAR archive for John.
 > 
 > **<font color=red>john</font> forjohn.txt**</br>
 > Crack RAR archive password.

## ZIP


 > 
 > **<font color=red>zip2john</font> myFile.zip <font color=red>\></font> forjohn.txt**</br>
 > Prepare ZIP archive for John.

 > 
 > **<font color=red>john</font> forjohn.txt**</br>
 > Crack ZIP archive password.
