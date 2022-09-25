---
title: HASHCAT
summary: A really fast password cracker.
description: A really fast password cracker.
---

[https://github.com/hashcat/hashcat](https://github.com/hashcat/hashcat)

## HASHCAT Mods

---

### Dictionary Mode (-m 0)


 > 
 > **<font color=red>hashcat -a 0 -m </font>0 “myHash” <font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Dictionary attack.

---

### Combinator Mode (-m 1)

https://hashcat.net/wiki/doku.php?id=combinator_attack

 > 
 > **<font color=red>hashcat -a 1 -m</font> 0 <font color=red>"</font>myHash<font color=red>"</font> myPrefix.txt <font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Dictionary attack with a prefix.

---

### Mask Mode (-m 3)

https://hashcat.net/wiki/doku.php?id=mask_attack 

#### Jokers

 > 
 > **<font color=red>?l</font>**</br>
 > abcdefghijklmnopqrstuvwxyz
 > 
 > **<font color=red>?u</font>**</br>
 > ABCDEFGHIJKLMNOPQRSTUVWXYZ
 > 
 > **<font color=red>?d</font>**</br>
 > 0123456789
 > 
 > **<font color=red>?h</font>**</br>
 > 0123456789abcdef
 > 
 > **<font color=red>?H</font>**</br>
 > 0123456789ABCDEF
 > 
 > **<font color=red>?s</font>**</br>
 > «space»!"#$%&'()\*+,-./:;\<=>?@\[\]^\_\`{|}~
 > 
 > **<font color=red>?a</font>**</br>
 > ?l?u?d?s
 > 
 > **<font color=red>?b</font>**</br>
 > 0x00 - 0xff

#### Exemples

 > 
 > **<font color=red>hashcat -a 3 -m</font> 0 <font color=red>"</font>myHash<font color=red>" ?l?l?l?l</font>**</br>
 > Brute force from aaaa to zzzz.

 > 
 > **<font color=red>hashcat -a 3 -m</font> 0 <font color=red>"</font>myHash<font color=red>" "passBegining?l?l?l?l"</font>**</br>
 > Brute force from passBeginingaaaa to passBeginingzzzz.

## HASHCAT Flags


 > 
 > **<font color=red>-a</font>**</br>
 > Attack mode (ex: 0 = straight dictionary list).
 > 
 > **<font color=red>-m</font>**</br>
 > Hashing type (ex: 1800 = MD5).
 > 
 > **<font color=red>-o</font>** myOutFile</br>
 > Store output info in myFile.

## HASHCAT Hash Type

https://hashcat.net/wiki/doku.php?id=example_hashes

 > 
 > **<font color=red>-m 0</font>**</br>
 > MD5.
 > 
 > **<font color=red>-m 500</font>**</br>
 > MD5crypt, MD5 (Unix), Cisco-IOS.
 > 
 > **<font color=red>-m 1800</font>**</br>
 > SHA256 Unix.
 > 
 > **<font color=red>-m 1000</font>**</br>
 > NTLM.
 > 
 > **<font color=red>-m 1100</font>**</br>
 > MS Cache - DCC (Domain Cached Credentials).
 > 
 > **<font color=red>-m 2100</font>**</br>
 > MS Cache - DCC2 (Domain Cached Credentials 2).
 > 
 > **<font color=red>-m 13000</font>**</br>
 > RAR.
 > 
 > **<font color=red>-m 13600</font>**</br>
 > WinZip.

## HASHCAT Exemples


 > 
 > **<font color=red>hashcat -a 0 -m 1100 0 '</font>15a57c379ebdfea572ad1ff91eb6ef0c:Administrator<font color=red>'</font> <font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Crack DCC (Domain Cached Credentials) hash.


 > 
 > **<font color=red>zip2john</font> myFile.zip <font color=red>\></font> forhashcat.txt**</br>
 > Remove name of the file and archive from the hash (at the beginning and the end).

 > 
 > **<font color=red>hashcat -a -m 13600</font> forhashcat.txt <font color=lightblue>/usr/share/wordslist/rockyou.txt</font>**</br>
 > Crack ZIP archive password.
