# wired-Gunisha-ECE
Hi. Following is my bandit writeup:
Bandit Level 0 -> 1
-------------------
*item-Logged in to the Bandit game using SSH with the command "ssh bandit0@bandit.labs.overthewire.org" and the password "bandit0".  
*item-Used the 'ls' command to list all files in the home directory and found the "readme" file.  
Used the 'cat' command to read the file's contents and found the password with "cat readme".  
***Password - ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If***

Bandit Level 1 -> 2
-------------------
Logged into level 2 of Bandit using SSH with the command "ssh bandit1@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list all files in the home directory and found the "-" file.
Used the 'cat' command to read the file's contents and found the password with "cat < -".
Alternatively, "cat ~/-" could also be used to read the file's contents. Here "~/" represents the home directory.
Password - 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

Bandit Level 2 -> 3
-------------------
Logged into level 3 of Bandit using SSH with the command "ssh bandit2@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list files in the home directory and found the file "spaces in this file name".
Used the 'cat' command to read the file's contents and found the password with "cat cat spaces\ in\ this\ filename".
Password - MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

Bandit Level 3 -> 4
-------------------
Logged into level 4 of Bandit using SSH with the command "ssh bandit3@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list the directory "inhere".
Used the 'cd' command to enter the "inhere" directory.
Used the 'ls -a' command to list all files in this directory and found the hidden file "...Hiding-From-You".
Used the 'cat' command to read the file's contents and found the password with "cat ...Hiding-From-You".
Password - 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

Bandit Level 4 -> 5
-------------------
Logged into level 5 of Bandit using SSH with the command "ssh bandit4@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list files and directories and found the "inhere" directory.
Used the "ls inhere" to list all files in the "inhere" directory.
Used the 'file' command to list types of files in the directory with "file inhere/*".

Output - bandit4@bandit:~$ file inhere/*
inhere/-file00: data
inhere/-file01: data
inhere/-file02: data
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: data

We can see that -file07 is the only human readable file in the directory.
Used "cat inhere/-file07" to read the file's contents and found the password.
Password - 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

Bandit Level 5 -> 6
-------------------
Logged into level 6 of Bandit using SSH with the command "ssh bandit5@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list the directory "inhere".
Used the find command to find files that are human-readable, 1033 bytes in size and not executable with "find inhere -type f -size 1033c ! -executable" which output the file "inhere/maybehere07/.file2".
Used the 'cat' command to read the file's contents and found the password with "cat inhere/maybehere07/.file2".
Password - HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

Bandit Level 6 -> 7
-------------------
Logged into level 7 of Bandit using SSH with the command "ssh bandit6@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the find command to find files somewhere on the server that is owned by user bandit7, owned by group bandit6 and is 33 bytes in size with "find / -type f -user bandit7 -group bandit6".
Whilst it still gives the solution, it gives permission errors which can be fixed by adding an argument "2>/dev/null", i.e, "find / -type f -user bandit7 -group bandit6 2>/dev/null".
Output - "/var/lib/dpkg/info/bandit7.password"
Used the 'cat' command to read the file's contents and found the password with "cat /var/lib/dpkg/info/bandit7.password".
Password - morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

Bandit Level 7 -> 8
-------------------
Logged into level 8 of Bandit using SSH with the command "ssh bandit7@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list the file "data.txt".
By using 'cat' command, we can see that it is a very large file and finding the string "millionth" would be difficult.
Used 'grep' command to find string "millionth" in data.txt with the command "grep "millionth" data.txt".
Output - millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
Password - dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

Bandit Level 8 -> 9
-------------------
Logged into level 9 of Bandit using SSH with the command "ssh bandit8@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list the file "data.txt".
By using 'cat' command, we can see that it is a very large file and finding the unique string would be difficult.
Using 'sort' command with the 'uniq' command, we can identify the unique string in this huge file.
Used "sort data.txt | uniq -u" and found the password.
Password - 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

Bandit Level 9 -> 10
--------------------
Logged into level 10 of Bandit using SSH with the command "ssh bandit9@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list the file "data.txt".
Used the 'strings' command along with 'grep' command to search for the string with "==".
Output - bandit9@bandit:~$ strings data.txt | grep ===
\a!;========== the
========== passwordf
========== isc
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

Password - FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

Bandit Level 10 -> 11
---------------------
Logged into level 11 of Bandit using SSH with the command "ssh bandit10@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list the file "data.txt".
Used the command "base64 -d data.txt" to decode the base64 encoded file.
Password - dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

Bandit Level 11 -> 12
---------------------
Logged into level 12 of Bandit using SSH with the command "ssh bandit11@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used the 'ls' command to list the file "data.txt".
Using 'cat' command, we can see the contents of this file. It contains a cipher called ROT13.
ROT13 is a simple substitution cipher that replaces a letter with the 13th letter after it.
Used "cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'" to decode the cipher.
Password - 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

Bandit Level 12 -> 13
---------------------
Logged into level 13 of Bandit using SSH with the command "ssh bandit12@bandit.labs.overthewire.org" and the password obtained from the previous level.
As instructed in the website, I made a temporary directory using "mktemp -d".
It is mentioned that it is a hexdump of a file that has been repeatedly compressed.
Used "cp data.txt /tmp/tmp.NvccWeOZ2F" to copy the data.txt to this temporary directory to create new files and directories with sufficient permissions.
Used "cd /tmp/tmp.NvccWeOZ2F" to change to the temporary directory.
Used "xxd -r data.txt data" to reverse the hexdump into a new file called "data".
Used "file data" to find out the type of file of "data".
Output - gzip compressed data, was "data2.bin"
Used "mv data data.gz" to change its file extension to a gzip compressed archive.
Used "gzip -d data.gz" to decompress this archive, which output a file called "data".
Used "file data" to find out the type of file of "data".
Output - bzip2 compressed data, block size = 900k
Used "mv data data.bz2" to change its file extension to a bzip2 archive.
Used "bzip2 -d data.bz2" to decompress this archive, which output a file called "data".
Used "file data" to find out the type of file of "data".
Output - gzip compressed data, was "data4.bin"
Used "mv data data.gz" to change its file extension to a gzip compressed archive.
Used "gzip -d data.gz" to decompress this archive, which output a file called "data".
Used "file data" to find out the type of file of "data".
Output - POSIX tar archive (GNU)
Used "mv data data.tar" to change its file extension to a tar archive.
Used "tar -xvf data.tar" to decompress this archive, which output a file called "data5.bin".
Used "file data5.bin" to find out the type of file of "data5.bin".
Output - data5.bin: POSIX tar archive (GNU)
Used "mv data5.bin data5.tar" to change its file extension to a tar archive.
Used "tar -xvf data5.tar" to decompress this archive, which output a file called "data6.bin".
Used "file data6.bin" to find out the type of file of "data6.bin" is.
Output - data6.bin: bzip2 compressed data, block size = 900k
Used "data6.bin data6.bz2" to change its file extension to a bzip2 archive.
Used "bzip2 -d data6.bz2" to decompress this archive, which output a file called "data6".
Used "file data6" to find out the type of file of "data6" is.
Output - data6:     POSIX tar archive (GNU)
Used "mv data6 data6.tar" to change its file extension to a tar archive.
Used "tar -xvf data6.tar" to decompress this archive, which output a file called "data8.bin".
Used "file data8.bin" to find out the kind of file of "data8.bin" is.
Output - data8.bin: gzip compressed data, was "data9.bin"
Used "mv data8.bin data8.gz" to change its file extension to a gzip archive.
Used "gzip -d data8.gz" to decompress this archive, which output a file called "data8".
Used "file data8" to find out the kind of file of "data8" is.
Output - data8:     ASCII text
Used "cat data8" to read the contents of this file and found a password.
Password - FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

Bandit Level 13 -> 14
---------------------
Logged into level 14 of Bandit using SSH with the command "ssh bandit13@bandit.labs.overthewire.org" and the password obtained from the previous level.
Used 'ls' command to list for files and found "sshkey.private".
Used "ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220" to connect to bandit14 using the SSHKEY.
After connecting to bandit14, used "cat /etc/bandit_pass/bandit14" to read the password.
Password - MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

Bandit Level 14 -> 15
---------------------
Logged into level 15 of Bandit using SSH with the command "ssh bandit14@bandit.labs.overthewire.org" and the password obtained from the previous level.
As mentioned in the website, used 'nc' command to connect to the 30000 port on localhost.
Used "nc localhost 30000" and entered the current level's password to obtain the next level's password.
Password - 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

Bandit Level 15 -> 16
---------------------
Logged into level 16 of Bandit using SSH with the command "ssh bandit15@bandit.labs.overthewire.org" and the password obtained from the previous level.
As mentioned in the website, the password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.
Read the manpages for openssl to understand how to connect to localhost port using SSL/TLS.
Used "openssl s_client -connect localhost:30001" to connect to the localhost port 30001 and entered the password to the current level, which output the password to the next level.
Password - kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

Bandit Level 16 -> 17
---------------------
Logged into level 17 of Bandit using SSH with the command "ssh bandit16@bandit.labs.overthewire.org" and the password obtained from the previous level.
As mentioned in the website, the credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000.
Used 'man' command to read manpages of commands we may need to solve this level.
Found command "nmap" which is an open source tool for network exploiatation and security auditing and was designed to rapidly scan large networks.
Used "nmap -p 31000-32000 localhost" to scan through the ports.

Output - Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-08-21 20:15 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00047s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Used "openssl s_client -connect" for each port listed above.
Ports 30146, 31691, 31960 did not connect.
Port 31518 did not read the password.
Port 31790 connected with "openssl s_client -ign_eof -connect localhost:31790", and output a ssh key when password to current level was input.

Output -
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

Made a temp dir with "mktemp -d".
Used "cd /tmp/tmp.BbZyNvQxjV"
Used "touch sshkey" to create a file called "sshkey".
Used "chmod 700 sshkey" to change the file's permissions to be editable.
Used "nano sshkey" to edit the text and added the RSA PRIVATE KEY to this text.
Saved ssh key on a file called "sshkey" in the temp directory.

Completed Level 16 -> 17.

Bandit Level 17 -> 18
---------------------

Used the "sshkey" from previous level and used "sshkey -i sshkey bandit17@bandit.labs.overthewire.org -p 2220" to login to Level 18.
The home directory contains two files, passwords.new and passwords.old.
Used "diff passwords.new passwords.old" to find out the only line that has been changed between passwords.old and passwords.new.
Password - x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO.

Bandit Level 18 -> 19
---------------------

Logged into level 19 of Bandit using SSH with the command "ssh bandit18@bandit.labs.overthewire.org -p 2220" and the password obtained from the previous level.
Modified .bashrc is logging us out when logging in with ssh.
Used "ssh bandit18@bandit.labs.overthewire.org -p 2220 ls -a" to list for
Output - .bash_logout .bashrc .profile readme
Cannot change .bashrc as upon logout server is reset and changes would not be saved.
Used "ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme" to read the readme file.
Found password.
Password - cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

Bandit Level 19 -> 20
---------------------

Logged into level 20 of Bandit using SSH with the command "ssh bandit19@bandit.labs.overthewire.org -p 2220" and the password obtained from the previous level.
Used "ls -l" to list for files.
Used "file bandit20-do" to find type of file.

Output - bandit20-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=368cd8ac4633fabdf3f4fb1c47a250634d6a8347, for GNU/Linux 3.2.0, not stripped

Used "./bandit20-do ls /etc/bandit_pass/" to list files.
Output - bandit0   bandit12  bandit16  bandit2   bandit23  bandit27  bandit30  bandit4  bandit8
bandit1   bandit13  bandit17  bandit20  bandit24  bandit28  bandit31  bandit5  bandit9
bandit10  bandit14  bandit18  bandit21  bandit25  bandit29  bandit32  bandit6
bandit11  bandit15  bandit19  bandit22  bandit26  bandit3   bandit33  bandit7

Used "./bandit20-do cat /etc/bandit_pass/bandit20" to read file contents.
Password - 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

Bandit Level 20 -> 21
---------------------

Logged into level 21 of Bandit using SSH with the command "ssh bandit20@bandit.labs.overthewire.org -p 2220" and the password obtained from the previous level.
Used "ls" to list for files.
Output - suconnect
Used "file suconnect" to find type.

Output - suconnect: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=4c95669a71860e303b714721dde9020213ad3c9a, for GNU/Linux 3.2.0, not stripped

As mentioned in the website, the binary makes a connection to the localhost port that we specify and reads the current level's password. So echo, nc commands are required. So this port has the current password and when connected with suconnect, it reads bandit20 password and outputs next level password. -l is used to specify port for listening.

Used "echo 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO | nc -l -p 2024 &" to start server to listen on specific port and '&' to run in background.
Used "./suconnect 2024" to connect to 2024 port.

Output - Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt

Password - EeoULMCra2q0dSkYj561DX7s1CpBuOBt

Bandit Level 21 -> 22
---------------------

Logged into level 22 of Bandit using SSH with the command "ssh bandit21@bandit.labs.overthewire.org -p 2220" and the password obtained from the previous level.
Used 'man' to read about cron, crontab and crontab(5).
Used "ls /etc/cron.d" to list files in directory.
Used "cat /etc/cron.d/cronjob_bandit22" to read its contents.

Output - @reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null

It is running a script in /usr/bin.
Used "cat /usr/bin/cronjob_bandit22.sh" to read file contents.

Output - #!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

Used "cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv" to read file contents which contained the password.
Password - tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q


