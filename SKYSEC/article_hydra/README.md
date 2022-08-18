WHAT İS HYDRA?
Weak passwords are still big problem in security. it is becoming easier to cracking algorithms with brute-forcing which is a major kind of attack. Hydra is a parallelized login cracker which supports many of protocols to attack remotely. With Hydra, it is getting faster and flexible and there is a chance to add new modules easily. Hydra uses wordlists to attack systems. Wordlists, contains most used passwords and we can customize our own wordlists to attack specific persons. In this case, this situation shows the importance of using a strong password.

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img1.jpeg)]

the list of all protocols supported by hydra.
Hydra is a pre-installed tool in Kali Linux. You can check the usage of Hydra with using this command. This page gives us the knowledge about parameters which we can use with Hydra tool:

#hydra -h

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img2.jpeg)]

To brute-force ssh username and password

#hydra ssh -l -P -s 22 -vV
We have username and password list to attack the target by using Hydra. You can access the wordlist files with this directory (for instance rockyou.txt file iz zipped. You have to unzip to use.)
cd /usr/share/wordlists

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img3.jpeg)]


To brute-force FTP username and password:

#hydra -L -P ftp://
-l : input login(not the list of usernames)
-L: username list
-p: if you will try single password
-P: list of passwords to do brute-forcing
-v : gives us details
-s : we can add the spesific ports that we want to attack with that parameter
-S: If it is possible, Hydra will try to connect with SSL with that parameter
-M: We will specified the location of the list of ports of the servers with this parameter

There is no difference between ssh and ftp connections usage . Parameters are same.
To brute-force telnet username and password:

#hydra -l -p telnet://
xHydra
Hydra also has interface page name that xHydra. You can open the xHydra page in terminal with “xhydra” command. In this interface you can pick the protocols and ports and other options from there. All the options are same with Hydra.

WORDLISTER TOOL
Firstly, we should install the Wordlister.
git clone https://github.com/4n4nk3/Wordlister.git command will help us.

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img4.jpeg)]


python3 wordlister.py –help
This command will give us options about how we can use the tool.

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img5.jpeg)]

We must have input word list to give Python to make wordlister with all combinations.
Then, we will give the details. For instance, we can choose the character size. Like you have to choose minimum 6 character for passwords.
python3 wordlister.py –input list.txt –perm 2 –min 6 –max 32
this command perm command tells us max 2 words can be conbined on the same possible password.

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img6.jpeg)]

We put the words in a txt file. Then run the command.

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img7.jpeg)]

We have the txt file that contains combinations.

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img8.jpeg)]


Using Leet mod
python3 wordlister.py –input input.txt –perm 2 –min 6 –max 32 –leet

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img9.jpeg)]
[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img10.jpeg)]


Using cap option to capitalize the first letter:
python3 wordlister.py –input list.txt –perm 2 –min 6 –max 32 –cap

[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img11.jpeg)]
 
Transform every letter in a word into uppercase:
python3 wordlister.py –input list.txt –perm 2 –min 6 –max 32 –up
 
[![site](https://github.com/sulingunana/article/tree/main/SKYSEC/article_hydra/img/img12.jpeg)]