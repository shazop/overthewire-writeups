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














