# NATAS Walkthrough
A brief guide to solving Natas Challenges on the OverTheWire platform.

## Natas answers for levels 1 - 15
### Level 0 -> 1
Credentials are username - _natas0_	and password - _natas0_

> In level 0, after logging in, right-click on the webpage to view the source code. The password for next level will be mentioned within a comment in the source code.
 
### Level 1 -> 2
credentials are username - _natas1_	and password - _g9D9cREhslqBKtcA2uocGHPfMZVzeFK6_

> This level is similar to the previous level, only that right-click is now blocked. So instead we use the keyboard shortcut (_usually **ctrl+shift+c**, but could be different in the browser that you are using)  

### Level 2 -> 3
Credentials are username - _natas2_ and password - _h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7_

> We can view the source code at this level, but there are no comments. We do find another directory referenced in the source code as `<img src='files/pixel.png>` indicating that there is another directory where files exist. So you add the directory `/files` to the current url. You should see a list of files in that directory and notice there is another file named _users.txt_. You should be able to find the password for the next level when reading this file.

### Level 3 -> 4
Credentials are username - _natas3_	 and password - _G6ctbMJ5Nb4cbFwhpMPSvxGHhQ7I6W8Q_

> In the source code of this webpage, we find a comment that says `<!-- No more information leaks!! Not even Google will find it this time... -->` This hints us to look at the **_robots.txt_** file. So you add `/robots.txt` to the url to view that file. This file tells 
search engines which directories they can or cannot crawl on the website. In this file, we find a directory that has not been allowed for crawling by bots, `s3cr3ts`. Now we replace the `/robots.txt` with the new found directory, and find `users.txt` file, similar to previous challenge. Here you will find password for the next level.

### Level 4 -> 5
Credentials are username - _natas4_	 and password - _tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm_

> This level would require you to understand how to use Burpsuite (or other tool to manipulate headers). After logging into the website using the credentials found in the previous challenge, capture the headers that were sent in the GET request. Now, you will need to change the natas level from `natas4...(rest of the value is same)` to `natas5...(rest of the value is same as original)`. After changing the URL Referrer, send the GET request with the modified headers. You should be able to view the password for next level on the page content that gets returned to the request made. 

natas5	Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD

natas6	fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR

natas7	jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr 

natas8	a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB

natas9 	Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd

natas10	D44EcsFkLxPIkAAKLosx8z3hxX1Z4MCE

natas11	1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg

natas12	YWqo0pjpcXzSIl5NMAVxg12QxeC1w9QG

natas13	lW3jYRI02ZKDBb8VtQBU1f6eDRo6WEj9

natas14	qPazSJBmrmU7UQJv17MHk1PGC4DxZMEP

natas15	TTkaI7AWG4iDERztBcEyKV7kRXH1EZRB

natas16 TRD7iZrd5gATjj9PkPEuaOlfEjHqj32V

