---
title: JOHN
summary: An advanced offline password cracker.
description: An advanced offline password cracker.
---

**[https://github.com/openwall/john](https://github.com/openwall/john)**

## Basis


 > 
 > **<font color=red>john --wordlist=</font>/usr/share/wordlists/rockyou.txt hash.txt**</br>
 > Crack unknown hash.

## Flags


 > 
 > **<font color=red>--fork=</font>4**</br>
 > Parallelization

## Unshadow


 > 
 > **<font color=red>unshadow /etc/passwd /etc/shadow ></font> unshadowd.txt**</br>
 > Prepare passwd and shadow file for John.
 > 
 > **<font color=red>john unshadow.txt --wordlist=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Crack user passwords.
 > 
 > **<font color=red>john --show</font> unshadow.txt**</br> 
 > Display cracked passwords.

## Private Key Passphrase


 > 
 > **<font color=red>/usr/share/john/ssh2john.py</font> private_key <font color=red>\></font> forjohn.txt**</br>
 > Prepare private key for John.
 > 
 > **<font color=red>john --wordlist=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font> forjohn.txt**</br>
 > Crack private key passphrase.

## JWT


 > 
 > **<font color=red>john --format=</font>HMAC-SHA512 jwt.txt <font color=red></font>**</br>
 > Brute force JWT's key used for signature. Choose the `alg` used by the token (e.g. `HMAC-SHA256`, `HMAC-SHA512`, ...).

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
