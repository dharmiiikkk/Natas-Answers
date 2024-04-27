# NATAS Walkthrough
A brief guide to solving NATAS Challenges on the OverTheWire platform. 

_Note: From challenge level 9 and above, I am just writing the hints that I noted while solving the challenges, which I used to write Python scripts (except for Challenge levels 12 and 13) that just scrapped the passwords. I hope to write a clearer and more beginner-friendly guide shortly._

Happy learning :)

## Natas answers for levels 1 - 15
### Level 0 -> 1
>Credentials are username - _natas0_	and password - _natas0_

In level 0, after logging in, right-click on the webpage to view the source code. The password for next level will be mentioned within a comment in the source code.
 
### Level 1 -> 2
>credentials are username - _natas1_	and password - _g9D9cREhslqBKtcA2uocGHPfMZVzeFK6_

This level is similar to the previous level, only that right-click is now blocked. So instead we use the keyboard shortcut (_usually **ctrl+shift+c**, but could be different in the browser that you are using)  

### Level 2 -> 3
>Credentials are username - _natas2_ and password - _h4ubbcXrWqsTo7GGnnUMLppXbOogfBZ7_

We can view the source code at this level, but there are no comments. We do find another directory referenced in the source code as `<img src='files/pixel.png>` indicating that there is another directory where files exist. So you add the directory `/files` to the current url. You should see a list of files in that directory and notice there is another file named _users.txt_. You should be able to find the password for the next level when reading this file.

### Level 3 -> 4
>Credentials are username - _natas3_	 and password - _G6ctbMJ5Nb4cbFwhpMPSvxGHhQ7I6W8Q_

In the source code of this webpage, we find a comment that says `<!-- No more information leaks!! Not even Google will find it this time... -->` This hints us to look at the **_robots.txt_** file. So you add `/robots.txt` to the url to view that file. This file tells 
search engines which directories they can or cannot crawl on the website. In this file, we find a directory that has not been allowed for crawling by bots, `s3cr3ts`. Now we replace the `/robots.txt` with the new found directory, and find `users.txt` file, similar to previous challenge. Here you will find password for the next level.

### Level 4 -> 5
>Credentials are username - _natas4_	 and password - _tKOcJIbzM4lTs8hbCmzn5Zr4434fGZQm_

This level would require you to understand how to use Burpsuite (or other tool to manipulate headers). After logging into the website using the credentials found in the previous challenge, capture the headers that were sent in the GET request. Now, you will need to change the natas level from `natas4`(rest of the value is same) to `natas5`(rest of the value is same as original). After changing the URL Referrer, send the GET request with the modified headers. You should be able to view the password for next level on the page content that gets returned to the request made. 

### Level 5 -> 6
>Credentials are username - _natas5_ and password - _Z0NsrtIkJoKALBCLi5eqFfcRN82Au2oD_

This level is similar to previous level. The headers must be captured, and the login status must be changede from `False` to `True`. 

### Level 6 -> 7
>Credentials are username - _natas6_	and password - _fOIvE0MDtPTgRhqmmvvAOt2EfXR6uQgR_

This level requires you to do more digging on the website. If you view the source code, there is a hint to the answer in the `/includes/secret.inc` page that is being referred to match the entered value. When you view that page, it is blank. This will confuse the attacker. However the referred variable in the source code of the main page is from the `secrets.inc` page, so there must be a variable with the correct value to unlock the password for the next level. If you view the source code of the blank page at `/includes/secrets.inc` you should find the variable that has the "secret" value that has been commented. 

### Level 7 -> 8
>Credentials are username - _natas7_ and password - _jmxSiH3SP6Sonf8dv66ng8v1cIEdjXWr_

The hint to find the answer that will give us the password is also in the source code. This time, the hint is direct and says that `<!-- hint: password for webuser natas8 is in etc/natas_webpass/natas8 -->`. This means that all we need to do is access this directory on their server to view the password for the next level. If you have used Linux before, then you must be familiar with using the `..` to change the working directory to the parent directory. If you haven't I would suggest you google about it and learn more, if possible try it out to understand better. There is web vulnerability called Local File Inclusion, that allows a user to access the local files on a server using the `../` to go to the parent directory and then enter the directory that we want to view. When you view the "home" or "about" page, notice the keyword `?page=` in the URL. This will query the webserver to view the page mentioned after this keyword. So when we add the string `../../../../../../../etc/natas_webpass/natas8` after the `?page=` string in the URL and hit enter, the webpage should show the password for the next level. 

### Level 8 -> 9
>Credentials are username - _natas8_	and password - _a6bZCNYwdKqN5cGP11ZdtPg0iImQQhAB_

This time, you see a form field with a submit button. Similar to the previous challenges, we again begin by viewing the source code of the index page. Upon analyzing the source code, we understand that an encrypted key is already written in the source code. The encoded string has been encrypted using the function defined in the source code. 
`decodedstr = base64.b64decode(bytes.fromhex(encodedstr)[::-1]).decode('utf-8')`
### Level 9 -> 10
>Credentials are username - _natas9_  and password - _Sda6t0vkOPkM8YeOZkAGVhFoaplvlJFd_

inject the form field; hint " ; cat /etc/natas_webpass/natas10*"

### Level 10 -> 11
>Credentials are username - _natas10_	and password - _D44EcsFkLxPIkAAKLosx8z3hxX1Z4MCE_

inject the form field without ";", instead use "."

### Level 11 -> 12
>Credentials are username - _natas11_	and password - _1KFqoJXi6hRaPluAmk8ESDW4fSysRoIg_

XOR encryption

### Level 12 -> 13
>Credentials are username - _natas12_	and password - _YWqo0pjpcXzSIl5NMAVxg12QxeC1w9QG_

upload file, go to inspect > elements> change random file name

### Level 13 -> 14
>Credentials are username - _natas13_	and password - _lW3jYRI02ZKDBb8VtQBU1f6eDRo6WEj9_

add image exif headers and repeat for natas12

### Level 14 -> 15
>Credentials are username - _natas14_	and password - _qPazSJBmrmU7UQJv17MHk1PGC4DxZMEP_

sql injection - admin | " or "1"="1

### Level 15 -> 16
>Credentials are username - _natas15_	and password - _TTkaI7AWG4iDERztBcEyKV7kRXH1EZRB_

Blind SQL injection 

Credentials for the next challenge which is level 16 -> 17 are username - _natas16_ and password - _TRD7iZrd5gATjj9PkPEuaOlfEjHqj32V_
