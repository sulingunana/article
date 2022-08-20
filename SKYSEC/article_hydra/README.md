# WHAT IS HYDRA?

Weak passwords are still big problem in security. it is becoming easier to cracking algorithms with brute-forcing which is a major kind of attack. Hydra is a parallelized login cracker which supports many of protocols to attack remotely. With Hydra, it is getting faster and flexible and there is a chance to add new modules easily. Hydra uses wordlists to attack systems. Wordlists, contains most used passwords and we can customize our own wordlists to attack specific persons. In this case, this situation shows the importance of using a strong password.

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img1.jpeg)

The list of all protocols supported by hydra.
Hydra is a pre-installed tool in Kali Linux. You can check the usage of Hydra with using this command. 
<br>
This page gives us the knowledge about parameters which we can use with Hydra tool:

```bash
hydra -h
```

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img2.jpeg)

To brute-force ssh username and password.

```bash
hydra ssh -l -P -s 22 -vV
```

We have username and password list to attack the target by using Hydra. You can access the wordlist files with this directory (for instance rockyou.txt file iz zipped. You have to unzip to use.)

```bash
cd /usr/share/wordlists
```

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img3.jpeg)


To brute-force FTP username and password:

```bash
hydra -L -P ftp://
```
-l : input login(not the list of usernames)
<br>
-L: username list
<br>
-p: if you will try single password
<br>
-P: list of passwords to do brute-forcing
<br>
-v : gives us details
<br>
-s : we can add the spesific ports that we want to attack with that parameter
<br>
-S: If it is possible, Hydra will try to connect with SSL with that parameter
<br>
-M: We will specified the location of the list of ports of the servers with this parameter
<br>
There is no difference between ssh and ftp connections usage . Parameters are same.
To brute-force telnet username and password:

```bash
hydra -l -p telnet://
```
### xHydra
Hydra also has interface page name that xHydra. You can open the xHydra page in terminal with “xhydra” command. In this interface you can pick the protocols and ports and other options from there. All the options are same with Hydra.

## WORDLISTER TOOL
Firstly, we should install the Wordlister.
```git
git clone https://github.com/4n4nk3/Wordlister.git 
```
command will help us.

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img4.jpeg)

```bash
python3 wordlister.py –help
```
This command will give us options about how we can use the tool.

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img5.jpeg)

We must have input word list to give Python to make wordlister with all combinations.
Then, we will give the details. For instance, we can choose the character size. Like you have to choose minimum 6 character for passwords.
<br>

```bash
python3 wordlister.py –input list.txt –perm 2 –min 6 –max 32
```
<br>
This command perm command tells us max 2 words can be conbined on the same possible password.

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img6.jpeg)

We put the words in a txt file. Then run the command.

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img7.jpeg)

We have the txt file that contains combinations.

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img8.jpeg)


### Using Leet mod:
```bash
python3 wordlister.py –input input.txt –perm 2 –min 6 –max 32 –leet
```

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img9.jpeg)
![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img10.jpeg)


### Using cap option to capitalize the first letter:
<br>

```bash
python3 wordlister.py –input list.txt –perm 2 –min 6 –max 32 –cap
```
<br>

![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img11.jpeg)

<br>

### Transform every letter in a word into uppercase:

```bash
python3 wordlister.py –input list.txt –perm 2 –min 6 –max 32 –up
``` 
<br>
![site](https://github.com/sulingunana/article/blob/main/SKYSEC/article_hydra/img/img12.jpeg)
