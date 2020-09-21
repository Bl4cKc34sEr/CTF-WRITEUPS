# Nahamcon CTF write-up

## Web

### Agent95

It says only agent95 is allowed, and that the older version of windows is required, so check for windows 95,  and change ‘User agent’ header by capturing the request in burp suite.
This is what gives us the flag:
**Windows 95; Microsoft x86_64**

<img src="https://github.com/devPlayer55221/CTF-writeups/blob/master/NahamCon%20CTF/images/agent95-2.png">

### Localghost

Open the source code of the page.  We can find a file used ‘jquery.jscroll2.js’. Open this js file and we get lots of code. Copy the contents of the variable "_0xbcec" 

<img src="https://github.com/devPlayer55221/CTF-writeups/blob/master/NahamCon%20CTF/images/localghost-1.png">

Using the find and replace we remove "\x" from the contents. Below is the hex we get after removing them.

<img src="https://github.com/devPlayer55221/CTF-writeups/blob/master/NahamCon%20CTF/images/localghost-2.png">
 
The result we get is a series of hex characters. Convert it to text and we again find some script.

<img src="https://github.com/devPlayer55221/CTF-writeups/blob/master/NahamCon%20CTF/images/localghost-3.png">

**SkNURntzcG9vb29va3lfZ2hvc3RzX2luX3N0b3JhZ2V9**

This is the thing which could give us the flag, as it looks odd in the code above. This is base 64 encoded. Decode it, and the flag is found.

<img src="https://github.com/devPlayer55221/CTF-writeups/blob/master/NahamCon%20CTF/images/localghost-4.png">
 
## Warmup

### Read the rules

Open the rules page and you get the flag in source code.

### CLIsay

Just download the file and through terminal, type : 
```strings clisay```
We get the flag. 

<img src="https://github.com/devPlayer55221/CTF-writeups/blob/master/NahamCon%20CTF/images/clisay-1.png">

### Metameme

The command is : 
```strings hackermeme.jpg | grep flag```

### UGGC

Using burp suite we capture the request, and find that the cookie is our input rotated by 13, therefore rotate admin by 13, and we get the flag. 
 
 <img src="https://github.com/devPlayer55221/CTF-writeups/blob/master/NahamCon%20CTF/images/uggc-1.png">

Here the user in cookie got set as ‘nopq’ when input is ‘abcd’. 
So, rotate ‘admin’ by 13, and the result is ‘nqzva’.
 
 <img src="https://github.com/devPlayer55221/CTF-writeups/blob/master/NahamCon%20CTF/images/uggc-2.png">

