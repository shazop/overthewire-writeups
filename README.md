# OverTheWire Bandit Writeups

# Level 0 and Level 0 → Level 1
## Level Goal

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is `bandit0` and the password is `bandit0`. Once logged in, go to the Level 1 page to find out how to beat Level 1.

### **Solution**:

Connecting to the given ssh hostname and password:
```ssh bandit0@bandit.labs.overthewire.org -p 2220```

Then enter the password: ```bandit0```

And we will get the shell access now just cat the readme file and here is over first **Flag:**

**Flag:** ```ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If```

<img width="807" height="199" alt="image" src="https://github.com/user-attachments/assets/b7ba836f-1739-435c-b0ab-d441e3220b97" />


# Level 1 → Level 2
## Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

### **Solution**:
After establishing ssh connection with the ssh key(lvl 0 flag).

Executing `ls` commmand we found that there is a file with `-` which is a special character 

So, just using `cat` command won't work here so we are using `cat ./-`

**Command:** `cat ./-`

**Flag:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

<img width="343" height="126" alt="image" src="https://github.com/user-attachments/assets/269bfbfb-aaa3-4fe1-b77e-08ba43df2b2d" />

# Level 2 → Level 3
## Level Goal
The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

### Solution:
Logged with the same ssh hostname with and the password(lvl 1 flag)
After listing the files, we can see that the file has spaces in between it.
So just typing as it is will cause errors, to get rid of it we need to use escape sequence which is \(back-slash after every word).

**Command:** ```cat -- --spaces\ in\ this\ filename--```

**Flag:** ```MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx```

Not sure why `--` is used before the filename

<img width="553" height="168" alt="image" src="https://github.com/user-attachments/assets/04bf9b9d-e3dc-4c2f-adb8-37de14573ec9" />

# Level 3 → Level 4
## Level Goal
The password for the next level is stored in a hidden file in the inhere directory.

### Solution:
After executing ls and file command we can find a directory called `inhere`.

After `cd` into the directory there is no files listed in the directory, In this situation we can use ls with a flag `-la` , which returns hidden files after executing the command we can find the hidden file. ```...Hiding-From-You```

Now just catting out the file gives as the lvl 3 **Flag:**

**Flag:** ```2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ```

<img width="743" height="286" alt="image" src="https://github.com/user-attachments/assets/8971ffb5-b71b-431c-80b3-9c904d9c1f6f" />

# Level 4 → Level 5
## Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Commands you may need to solve this level
ls , cd , cat , file , du , find

### Solution:
Here also there is the same directory ```inhere```

And inside the directory we can see lot of files with garbage data, for filtering that we can use a simple **Command:**

```file ./*``` - `*` asterisk prints all the files and file command returns the file type of the file.

Where `-file07` is the ascii text and we can get the flag

**Flag:** ```4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw```
<img width="884" height="397" alt="image" src="https://github.com/user-attachments/assets/992c53a2-763a-433a-a3c4-02157271424a" />

# Level 5 → Level 6
## Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

### Solution: 

In this Level they have give some properties, in which we to filter out the file and get the flag.
They have given the file is 

readable

1033 size

not executable 

So here is our **Command:** 

```find . -readable -size 1033c -not -executable```

**Explanation**
`find` - used for finding/filtering out specific files
`.` - which means find the file in the current directory
And rest is the given properties of the file

Which returns the right file, and catting it out gives the **Flag:**

**Flag:** ```HWasnPhtq9AVKe0dmk45nxy20cvUa6EG```

<img width="816" height="187" alt="image" src="https://github.com/user-attachments/assets/77ed9256-aa15-4994-8f43-0cd02cde7b0b" />

# Level 6 → Level 7
## Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size

### Solution:

Here also they have given the properties to find the flag file.

Using find command with the specific filters, we can find a file with no permission denied.

```find / -user bandit7 -group bandit6 -size 33c```


<img width="520" height="139" alt="image" src="https://github.com/user-attachments/assets/ce27cc23-3edf-40b3-bb6c-c90e2b6178fe" />


<img width="585" height="71" alt="image" src="https://github.com/user-attachments/assets/0223014f-f8f4-4295-9a9a-a59f246fc90e" />



**Flag:** ```morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj```

# Level 7 → Level 8
## Level Goal
The password for the next level is stored in the file data.txt next to the word **millionth**

### Solution
Here we have given a wordlist of username and password, And they have mentioned that username `millionth` has the flag 
So, using simple `grep` command we can filter the exact line:

**Command:**
```cat data.txt | grep 'millionth'```

<img width="475" height="125" alt="image" src="https://github.com/user-attachments/assets/96bb8c9e-257d-48be-98e2-7aacb1aaf2c2" />


**Flag:** ```dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc```

# Level 8 → Level 9
## Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

### Solution

Here we are using `sort` and `uniq` commands for sorting in ascending order and finding the unique occurence(only one repitition)

**Command:** `cat data.txt | sort | uniq -u`

<img width="499" height="75" alt="image" src="https://github.com/user-attachments/assets/d9712f0d-ffaf-4c31-82b4-0f65641350a9" />

**Flag:** ```4CKMh1JI91bUIZZPXDqGanal4xvAg0JM```

# Level  9 → Level 10
## Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

### Solution
Here we are given data.txt file, if we cat the file which returns garbage, So lets use `strings` command here

`strings` - used for filtering strings above 4 characters

**Command:** ```strings data.txt```

And here is our flag:

<img width="675" height="460" alt="image" src="https://github.com/user-attachments/assets/eb82115d-3f65-4b72-9fa7-e12d2c388772" />

**Flag:**  ```FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey```

# Level  10 → Level 11
## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data.

**Solution:**
When we cat the file we can see the string is ended with `==`(2 equal signs), which is a clear indication of base64 encoding we can decode that using the command `base64 -d `

**Command:** ```cat data.txt  | base64 -d```

<img width="640" height="155" alt="image" src="https://github.com/user-attachments/assets/de158adc-839b-452d-bd81-c82eedf93fb2" />

**Flag:** `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`


# Level  11 → Level 12
## Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

**Solution:**
Simple rot13 has been done so rot13 returns the flag

<img width="489" height="54" alt="image" src="https://github.com/user-attachments/assets/33f8e2fe-a668-4213-9375-2e3e00ad39e7" />

We can use cyberchef for decoding it:

<img width="727" height="678" alt="image" src="https://github.com/user-attachments/assets/cc5bb382-bc12-4319-8e32-3799878f3457" />

**Flag:** ```7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4```

# Level  12 → Level 13
## Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

### Solution
Here we can see a Hexdump stored in a text file

<img width="697" height="236" alt="image" src="https://github.com/user-attachments/assets/4b87a54e-7cd6-4520-b08d-c9d109878d1f" />

By using this command we can reverse the hexdump to executable file 

```cat data.txt | xxd -r > hexdump```

Before doing this make sure to copy the file .txt file to the /tmp/<any-dir-name>

After that using file command for finding the file of the reversed hexdump we can see that its a gzip file

<img width="1093" height="74" alt="image" src="https://github.com/user-attachments/assets/16d8c611-e160-42e2-8592-55178862ef11" />

The file is looped with gzip and bz2 zippers use this command multiple times and we should get a tar file.
Here are the commands to do so

```mv hexdump hexdump.gz```

```gzip -d hexdump.gz```

```bzip2 -d hexdump```

```tar -xvf hexdump```

After doing multiple times we can cat our flag:

```FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn```

<img width="558" height="133" alt="image" src="https://github.com/user-attachments/assets/cd34d410-4dda-4d47-8e4d-f8ff792b52fd" />

Tip: Use file command everytimke to determine the filetype for extracting

# Level  13 → Level 14
## Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.

Solution:

Here we can see a SSH key, to solve this lvl we need to simply connect to the localhost of the ssh server

```ssh -i sshkey.private -p 2220 bandit14@localhost```

Had an issue here 
<img width="829" height="463" alt="image" src="https://github.com/user-attachments/assets/268fdcb0-1b98-43fd-a130-58d44da0ea48" />

Flag: ```MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS```

# Bandit Level 14 → Level 15
## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

**Solution**:

In this challenge we need to netcat to the port 30000

Command: ```nc localhost 30000```

And enter the current lvl 14 password and we can see the lvl 15 flag is printed on the console

Flag: ```8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo```

<img width="376" height="85" alt="image" src="https://github.com/user-attachments/assets/dfc3a958-51db-4526-9956-f6f34586f0fa" />

# Bandit Level 15 → Level 16
## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

**Solution:**

Here we need to connect to the port 30001 with openssl

Commands:

```pass=8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo```

```openssl s_client -connect localhost:30001```

And enter your current password the new password will be printed

Flag: ```kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx```



<img width="512" height="287" alt="image" src="https://github.com/user-attachments/assets/1a199c70-7182-42dd-b01f-cb14444a719d" />

# Bandit Level 16 → Level 17
## Level Goal
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

**Solution**:

In this challenge we can see that there is port range from 31000 to 32000 in which we need to find the one which uses ssl and nc into it.

For that we can use the nmap tool.

Command:

```nmap localhost -p 31000-32000```

Which is used for finding open ports and we got 6 open ports, so lets find the service running on the open ports using this command

Command: 

```nmap localhost -p 31046,31518,31691,31790,31960 -sV -T4```

<img width="475" height="150" alt="image" src="https://github.com/user-attachments/assets/09e3d325-d9a6-4b04-9776-419871fd96a2" />

Then simply connect with openssl

Command:

```openssl s_client -connect localhost:31790 -ign_eof```

And a RSA key will show up

<img width="794" height="501" alt="image" src="https://github.com/user-attachments/assets/d87040db-18d7-4098-a2ca-5aa602bc8d70" />

Save that ssh key in a file like ssh_key.pem and thats our key for next lvl

```-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

# Bandit Level 17 → Level 18 
## Level Goal
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

**Solution:**

In this challenge one particular line is changed from password.old and saved as password.new which is the flag

Command:

```diff passwords.old passwords.new```

<img width="625" height="118" alt="image" src="https://github.com/user-attachments/assets/87b4634e-4e6b-45c0-9a6f-9aad09080e31" />

Flag: `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

# Bandit Level 18 → Level 19

## Level Goal
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

**Solution:**

Here the interactive terminal is off so we need to just add cat readme for printing the flag

Flag: ```cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8```

<img width="825" height="263" alt="image" src="https://github.com/user-attachments/assets/5fb48e78-d4c5-4da8-a4da-12e0a7283495" />

# Bandit Level 19 → Level 20
## Level Goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

**Solution:**

Here we can see a elf file from which we can command execution and we can see that in the permission only the ELF file have access to the bandit20 host

Command: ```./bandit20-do cat /etc/bandit_pass/bandit20```

Flag: `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`

# Bandit Level 20 → Level 21
## Level Goal
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

**Solution:**
































