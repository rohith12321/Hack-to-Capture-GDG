# Markup 
## Level 0 - Level 1
Typing the following command in the bash
```$ ssh bandit.labs.overthewire.org -p 2220 -l bandit0```
Then after reaching the home directory using ls to see the readme file and opening it from  ```$ cat readme ```, getting the password.
Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1 - Level 2
Using the  ```$ ls ``` command in the home directory, we find the '-' file, using  ```$ cat - ``` does not work, so after googling we obtain password using the ```$ cat ./- ``` command.
Password - 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2 - Level 3
First login using ``` $ ssh bandit.labs.overthewire.org -p 2220 -l bandit2 ``` and using the previous password.
Using ls we see a file name 'spaces in this filename', as opening is would not work directly we can use: 
```$ cat "spaces in this filename"```
Which gives us the password:  MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 3 - Level 4
Logging in the maching as before, we can see a directory called "inhere". Going inside is and viewing its contents using:
```console
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat "...Hiding-From-You"
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
We find nothing, so I figured the file must be hidden, so used the '-a' along with the last command to find the file "...Hiding-From-You" opening it we get the next password. 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4 - Level 5

Opening the inhere directory, we see 10 file named "-file00" to "-file09".
Opeing fileoo using `$ cat ./-file00`, we optain a weird terminal. After checking the filetype using `$ file ./-file00`, I found it was a data file. Then looking at the filetypes of all the files, only file07 had ascii text. Opeing it, we get the password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5 - Level 6
Opening the inhere directory, we find 20 folders which themselves contain many files, both hidden and visible. Checking the website for the level, I had to find the file which followed the following criteria: 
human-readable
1033 bytes in size
not executable
Thus after googling about the search commands and learning the filters using 
`$ find -type f -size 1033c`
to find a file of the size required, only a single file i.e "/maybehere07/.file2" was obtained. Checking the file for human readable using `$ file /maybehere07/.file2`, it was confirmed and containded the required password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG


## Level 6 - Level 7
We had to find a file which had a specific user and group as its owner in the whole server. After a little googling regarding the filters of the find command, I used the command:
`$ find / -user bandit7 -group bandit6`
to find the file searching from the root directory. After search, there were many results which had permission denied and only one file namely '/var/lib/dpkg/info/bandit7.password', was found by the find command. This file contained the password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Level 7 - Level 8
To find a pirticular text from the file "data.txt", i used the "grep" command.
Using: `$ grep -r millionth "data.txt" `, we obtain the password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 8 - Level 9
I needed to find the only password which was not repeated in the file. To do that, I used the sort and uniq commands. Using the sort command I sorted the passwords in order, so that repeated passwords were together. After that, I pipped the output to the uniq function using the -c argument. This allowed me to view how many times the different string were repeated. Out of them all only one was not repeated at all, giving us the password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
Command used: `$ sort data.txt | uniq -c`
Note: for sort and uniq, i read about them and their arguments using the GNU manual and online sources like GeeksforGeeks. I also understood the concept of Pipping beforehand and only used google to find the correct syntax to impliment it.

## Level 9 - Level 10
The password was preceded by multiple '=' signs, so I used the grep commands to search for multiple length of '=' symbol. Typing only: `$ grep ==== data.txt` gave the result:
`grep: data.txt: binary file matches`
Using the '-a' argument with grep, I found 3 lines which contained consecutive '='. Out of the three lines, only one of them had a password in front of the ===== text. This gave the password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Level 10 - Level 11
To decode the characters from base64, used the `$ base64` command like:
`$ base64 -d data.txt`
which gave: "The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr".

## Level 11 - Level 12
We needed to transform each character such that it becomes the character 13 places behind it. To do that I used the `$ tr` command. After reading the manual and learning about Rot13, I knew we had to convert a-m to n-z and vice-versa, for both lowercase and uppercase.
Using google to get the syntax right, used the command:
`$ cat data.txt |tr "A-Za-z" "N-ZA-Mn-za-m"
To transform the text inside data.txt, i got "The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4"

## Level 12 - Level 13
This level required us to decompress and de-hexdump a file continuiosly until we got the password. After creating a directory in /tmp, copied the data.txt file into it. After that, using the xxd command, we de-hexdump the file and save the result to another file. Then we check the filetype of this new file and decompress it using gzip (we had to first append the appropriate extention using mv command). Next we needed to decompress the file multiple times from either gzip, bzip2 or tar (determining this by checking the filetype of the new file created and applying the required extention when required). At last we obtain a data8 ASCII file, which contains the password.
The commands in order that I used are:
```console
bandit12@bandit:/tmp$ mkdir 12390
bandit12@bandit:/tmp$ cd
bandit12@bandit:~$ cp data.txt /tmp/12390
bandit12@bandit:~$ cd /tmp/12390
bandit12@bandit:/tmp/12390$ xxd -r data.txt data1.txt
bandit12@bandit:/tmp/12390$ file data1.txt
data1.txt: gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 574
bandit12@bandit:/tmp/12390$ mv data1.txt data1.gz
bandit12@bandit:/tmp/12390$ gzip -d data1.gz
bandit12@bandit:/tmp/12390$ ls
data1  data.txt
bandit12@bandit:/tmp/12390$ file data1
data1: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/12390$ bzip2 -d data1
bzip2: Can't guess original name for data1 -- using data1.out
bandit12@bandit:/tmp/12390$ file data1.out
data1.out: gzip compressed data, was "data4.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/12390$ mv data1.out data1.out.gz
bandit12@bandit:/tmp/12390$ gzip -d data1.out.gz
bandit12@bandit:/tmp/12390$ ls
data1.out  data.txt
bandit12@bandit:/tmp/12390$ file data1.out
data1.out: POSIX tar archive (GNU)
bandit12@bandit:/tmp/12390$ mv data1.out data1.tar
bandit12@bandit:/tmp/12390$ tar -xf data1.tar
bandit12@bandit:/tmp/12390$ ls
data1.tar  data5.bin  data.txt
bandit12@bandit:/tmp/12390$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/12390$ mv data5.bin data5.tar
bandit12@bandit:/tmp/12390$ tar -xf data5.tar
bandit12@bandit:/tmp/12390$ ls
data1.tar  data5.tar  data6.bin  data.txt
bandit12@bandit:/tmp/12390$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/12390$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/12390$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)
bandit12@bandit:/tmp/12390$ mv data6.bin.out data6.tar
bandit12@bandit:/tmp/12390$ tar -xf data6.tar
bandit12@bandit:/tmp/12390$ ls
data1.tar  data5.tar  data6.tar  data8.bin  data.txt
bandit12@bandit:/tmp/12390$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/12390$ mv data8.bin data8.gz
bandit12@bandit:/tmp/12390$ gzip -d data8.gz
bandit12@bandit:/tmp/12390$ ls
data1.tar  data5.tar  data6.tar  data8  data.txt
bandit12@bandit:/tmp/12390$ file data8
data8: ASCII text
bandit12@bandit:/tmp/12390$ cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

## Level 13 - Level 14
In this level, I had to login to bandit14 using the ssh key as the authentication. After reading how ssh key words and the ssh man, i found the -i argument, which allowed me to input the private key as authentication. After logging onto the bandit14 user, i just had to go to /etc/bandit_pass/bandit14 to get the password : MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

Commands used:
```console
$ ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
$ cat /etc/bandit_pass/bandit14
```
## Level 14 - Level 15
I just had to use the password obtained in the previos level and use the `$ nc` command to submit it like:
`$ nc localhost 30000`
`$ MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`
And recieve the password: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo







