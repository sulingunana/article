
# CYBORG

## we need information for server and web pages etc.

We used the following list of tools:
- Nmap
- gobuster
- dirb 
their command list is here
- dirb http://machine_IP
- sudo nmap -A -sV -O -p- 10.10.152.244
-  gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-1.0.txt -u http://machine_ip

we take results.

[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/1.png)](https://tryhackme.com/p/biyik)

[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/2.png)](https://tryhackme.com/p/biyik)

The results we got from the “dirb” command were /admin and /etc page.

# THE ADMIN PAGE


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/3.png)](https://tryhackme.com/p/biyik)


	- we can see other link to when my mouse on “download” button. And click&save In order to we analyze for folder and documents. Let’s extract file on my machine and go to “final_archive” document directory. And write “ls” command. We see that,


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/4.png)](https://tryhackme.com/p/biyik)

If you mind want open to all file you can learn some information for ctf. However we open the only main subject documents. So I am run that command “cat README” on terminal and I see borgbackup github and I installed on my machine. “borg extract path/to/final_archive::music_archive” 


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/5.png)](https://tryhackme.com/p/biyik)


$apr1$BpZ.Q.1m$F0qqPwHSOG50URuOVQTTn. 

We need a passphrase for key found So See other page look


# THE ETC PAGE IS


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/6.png)](https://tryhackme.com/p/biyik)


## click to passwd and see that:


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/7.png)](https://tryhackme.com/p/biyik)


## we search to hashcat example list on 


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/8.png)](https://tryhackme.com/p/biyik)

So I create passwd.hash documents while use to hashcat tool with -m 1600 parameters with passwd.hash. 


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/9.png)](https://tryhackme.com/p/biyik)


## And I got this result.


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/10.png)](https://tryhackme.com/p/biyik)

- squidward

### And we can look the home folder in and can find username and password for ssh.


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/11.png)](https://tryhackme.com/p/biyik)


YES THAT’S IT.




--- user flag ------
-ssh alex@machine_ıp

and for password S3cretP@g3 and login.

“Cat user.txt”  we found user flag.

---- Root flag -----

We run the “sudo -l” command to find out our permission and we see permission on etc/mp3backup/backup.sh script on (ALL:ALL) Permission. So we run this command “./etc/mp3backup/backup.sh -c /bin/bash” and you in root sign in but can’t any see command output to on terminal, because terminal on run script is write with root permission command but can’t read with root permission. However, Since we are running the “ -c /bin /bash” command, we can view the root directory in bash. Let’s look! So for can I that make, need a simple run a few command run.


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/12.png)](https://tryhackme.com/p/biyik)


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/13.png)](https://tryhackme.com/p/biyik)


# we can find googling q-2 and q-3


[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/a2.png)](https://tryhackme.com/p/biyik)

[![img](https://github.com/Onur-TURAN/H4CK-D/blob/main/THM/Cyborg/img/a3.png)](https://tryhackme.com/p/biyik)



