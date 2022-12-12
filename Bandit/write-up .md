# OverTheWire

# Bandit
 ## Level 0
 Login into the game using ssh
 Host: bandit.labs.overthewire.org
User: bandit0
 password: bandit0

 ```
 ssh bandit0@bandit.labs.overthewire.org -p 2220
 ```
  **What did I learn**
  Use of ssh command

## Level 0 →  Level 1
**How was it solved**
Done it with command cat
```
cat readme
```



**What did I learn**
Learn about cat command 

## Level 1→Level 2 

**How was it solved**
```ssh bandit1@bandit.labs.overthewire.org -p 2220
 ```
 First we make sure the file is in the folder by printing all the files
 ```
 bandit1@bandit:~$ ls
 ```
 Open dashed file name using cat ./- commands
 ```
 bandit1@bandit:~$ cat ./-
 ```
 
**what did i learn**
Usage of cat ./- command

## Level 2→Level 3
**How was it solved**
Using the command
``` cat spaces\in\this\filename```
or 
```cat "spaces in this filename"```

**What did I learn**
Open a file as there are spaces in the filename


## Level 3→Level 4

**How was it solved**
Using the commands 
```
cd inhere
ls -a
cat .hidden
```
**What did I learn**
view files that are in the directory using the ```ls``` command. Since we know the file is hidden we have to use the ```-a``` flag to view hidden files



## Level 4-Level 5
**How was it solved**
Tried to read files one by one with using cat and ./ used bacause filename starting with "-"
```
cd inhere
ls
cat ./-file07
```

##  Level 5-Level 6
**How was it solved**
Find size we use 'du' command and to get size in bytes we use '-b' to get size of all we use '-a'
```
ls
cd inhere
ls
ls -al * | grep -B 10 1033
cat maybehere07/.file2
```
**What did I learn**
du - estimate file space usage

## Level 6-Level 7
**How was it solved**
```
find / -type f -user bandit7 -group bandit6 -size 33c
/var/lib/dpkg/info/bandit7.password
cat /var/lib/dpkg/info/bandit7.password
```

## Level 7-Level 8
**How was it solved**
The password is next to the word "millionth" in the file .We can look for this pattern by using ```grep``` command
```
cat data.txt | grep millionth
```


**What did I learn**
Use of grep command

##  Level 8-Level 9
**How was it **
Use "sort" command for sorting and we use "unique" command to find line occurs only once with help of pipe to to make all in one line commandlved

```cat data.txt | sort | uniq -u```


**What did I learn**
Learn about 'unique' and 'sort' command

## Level 9-Level 10

**How was it solved**
In this file there is a few human-readable strings. We want to read this file using cat command

```cat data.txt | strings```

**What did I learn**
'string' command is used to find strings

## Level 10-Level 11

**How was it solved**
In this the data is base64 encoded. We can decode this using ```base64``` command. ```-d``` flag is usede to decode the data
```cat data.txt | base64 -d```
**What did I learn**
Learn about base64 and -d

## Level 11-Level 12
**How was it solved**
First read the file data.txt using cat command

```
cat data.txt

```
got a ciphertext
Decoded it online with "ROT13 decoder"

## Level 12-Level 13
**How was it solved**

```
ls
cat data.txt
mkdir /tmp/newfile666
cp data.txt /tmp/newfile666
cd /tmp/newfile666
xxd -r data.txt data
file data
mv data data.gz
gzip -d data.gz
file data
mv data data.bz2
bzip2 -d data.bz2
file data
mv data data.gz
gzip -d data.gz
file data
tar -x -f data
file data5.bin
tar -x -f data5.bin
file data6.bin
bzip2 -d data6.bin
file data6.bin.out
tar -x -f data6.bin.out
file data8.bin
mv data8.bin data8.gz
gzip -d data8.gz
file data8
cat data8
```

## Level 13-Level 14
**How was it**
We have SSH private key. We can use the SSH command with the ```-i``` flag to use the private key
```ssh -i sshkey.private bandit14@localhost```
WE have logged in as bandit14 we can confirm this by looking at your prompt

Get the password for the current user

```bandit14@bandit:~$ cat /etc/bandit_pass/bandit14```

## Level 14- Level 15
**How was it solved**
Used **nc** command to connect with port 30000 on localhost
```
nc localhost 30000
```
And gave the password of level 14
```fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq```
Output:

Correct! jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

Pass: jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
## Level 15- Level 16
**How was it**
```
openssl s_client -connect localhost:30001
```
After entering to the port , Gave previous password

```
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

```
**What did I learn**
learn about **openssl** command and **s_client** command

## Level 16 - Level 17
**How was it solved**

Using nmap -p command, we will perform a port scan to identify the open ports between the range of 31000 to 32000

```
 nmap -p 31000-32000 localhost

```

the output we received for

```
cat /etc/bandit_pass/bandit16 | openssl s_client -connect localhost:31790 -quiet

```

Got a private key

```
-----BEGIN RSA PRIVATE KEY-----
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

Save the key in a new folder

```
mkdir /tmp/name123         
cd /tmp/name123             

```

Using vim editor we will copy and paste the RSA private key into a file named, sshkey.private, under name123 folder

```
vim sshkey.private
```
```
cat sshkey.private
chmod 400 sshkey.private
sh -i sshkey.private bandit17@localhost -p2220
cat /etc/bandit_pass/bandit17
