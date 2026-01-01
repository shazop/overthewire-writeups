# Level 0 and Level 0 → Level 1
## Level Goal

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is `bandit0` and the password is `bandit0`. Once logged in, go to the Level 1 page to find out how to beat Level 1.

Commands you may need to solve this level
ssh

### **Solution**:

Connecting to the given ssh hostname and password:
```ssh bandit0@bandit.labs.overthewire.org -p 2220```

Then enter the password: ```bandit0```

And we will get the shell access now just cat the readme file and here is over first flag:

Flag: ```ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If```

<img width="807" height="199" alt="image" src="https://github.com/user-attachments/assets/b7ba836f-1739-435c-b0ab-d441e3220b97" />


# Level 1 → Level 2
## Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

Commands you may need to solve this level
ls , cd , cat , file , du , find

### **Solution**:
After establishing ssh connection with the ssh key(lvl 0 flag).

Executing `ls` commmand we found that there is a file with `-` which is a special character 

So, just using `cat` command won't work here so we are using `cat ./-`

Command: `cat ./-`

Flag: `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

<img width="343" height="126" alt="image" src="https://github.com/user-attachments/assets/269bfbfb-aaa3-4fe1-b77e-08ba43df2b2d" />

# Level 2 → Level 3
## Level Goal
The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

Commands you may need to solve this level
ls , cd , cat , file , du , find


### Solution:
Logged with the same ssh hostname with and the password(lvl 1 flag)
After listing the files, we can see that the file has spaces in between it.
So just typing as it is will cause errors, to get rid of it we need to use escape sequence which is \(back-slash after every word).

Command: ```cat -- --spaces\ in\ this\ filename--```

Flag: ```MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx```

Not sure why `--` is used before the filename

<img width="553" height="168" alt="image" src="https://github.com/user-attachments/assets/04bf9b9d-e3dc-4c2f-adb8-37de14573ec9" />

# Level 3 → Level 4
## Level Goal
The password for the next level is stored in a hidden file in the inhere directory.

Commands you may need to solve this level
ls , cd , cat , file , du , find

### Solution:
After executing ls and file command we can find a directory called `inhere`.

After `cd` into the directory there is no files listed in the directory, In this situation we can use ls with a flag `-la` , which returns hidden files after executing the command we can find the hidden file. ```...Hiding-From-You```

Now just catting out the file gives as the lvl 3 flag:

Flag: ```2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ```

<img width="743" height="286" alt="image" src="https://github.com/user-attachments/assets/8971ffb5-b71b-431c-80b3-9c904d9c1f6f" />

# Level 4 → Level 5
## Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Commands you may need to solve this level
ls , cd , cat , file , du , find

### Solution:
Here also there is the same directory ```inhere```

And inside the directory we can see lot of files with garbage data, for filtering that we can use a simple command:

```file ./*``` - `*` asterisk prints all the files and file command returns the file type of the file.

Where `-file07` is the ascii text and we can get the flag

Flag: ```4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw```
<img width="884" height="397" alt="image" src="https://github.com/user-attachments/assets/992c53a2-763a-433a-a3c4-02157271424a" />


