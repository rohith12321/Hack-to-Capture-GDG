# Writeup

## Level 0


Using ssh command to connect to the host on port 2220 with username bandit0 and password bandit0.This command would be used repeatedly,we have to just change numbers according to the level. 
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220
```

## Level 1
password - ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
used ls,got a file readme,accessed it using cat readme.
```bash
$ ls
$ cat readme
```
## Level 2
password - 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
Here we get '-' file on ls,but cat - wont work as it waits for keyboard input.
```bash
$ ls
$ cat ./
```
## Level 3
password - MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
On ls we get spaces in this filename,so we have to use following command.
```bash 
$ ls
$ cat "spaces in this filename"
```
## Level 4
password - 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
On ls got inhere directory,changed directory to inhere.Upon doing ls nothing appeared,so did ls -a(for hidden files) so got . .. and ...Hiding-From-You.Got password in ...Hiding-From-You.
```bash
$ ls
$ cd inhere
$ ls (got_nothing)
$ ls -a
$ cat ...Hiding-From-You
```
## Level 5
password - 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
On doing ls got inhere directory changed to it.Upon doing ls again got files named -file00 to -file09.Opened them one by one and found password in -file07.
```bash
$ ls
$ cd inhere
$ ls
$ cat ./-file07
```
## Level 6
password - HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
ls->inhere->ls got directories named maybehere00 to i think maybehere16.Then used find command with given conditions to get file path then used cat./extracted file path.
```bash
$ ls
$ inhere
$ ls
$ find . -type f -size 1033c ! -executable
$ cat./extracted file path
```
## Level 7
password - morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
did ls but found no files.Then used find with given conditions,got many files with permission denied message but one was open,used cat command on it and got the password.
```bash
$ ls
$ find / -user bandit7 -group6 -size 33c
$ cat /var/lib/dpkg/info/bandit7.password
```
## Level 8
password - dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
On doing ls got data.txt file.It had many word-password combination but to find password in front of "millionth" i used grep command.
```bash
$ ls
$ cat data.txt
$ grep "millionth" data.txt
```
## Level 9
password - 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM 
on doing ls got data.txt.since the password was unique i used sort and uniq command.
```bash
$ ls
$ cat data.txt
$ sort data.txt | uniq -u
```
## Level 10
password - FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
After ls got data.txt.Used cat data.txt and manually found string after many '=' signs.
```bash 
$ ls
$ cat data.txt
```
## Level 11
password - dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
Used base64 decoding by using -d command.
```bash
$ base64 -d data.txt
```

## Level 12
password - 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
used command for ROT13
```bash
$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
## Level 13
password - FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
created a working directory,then copied data.txt to working directory.used xxd to convert hexdump to binary form.used file to identify compression type,then used decompression commands,got a file data8,used cat to get the password.
```bash
$ mkdir /tmp/pradyumna
$ cd /tmp/pradyumna
$ cp ~/data.txt .
$ xxd -r data.txt data.bin
$ file data.bin
$ mv data.bin data.gz
$ gunzip data.gz
$ mv data data.bz2
$ bunzip2 data.bz2
$ mv data data.gz
$ gunzip data.gz
$ mv data data.tar
$ tar -xf data.tar
$ mv data5.bin data.tar
$ tar -xf data.tar
$ mv data6.bin data.bz2
$ bunzip2 data.bz2
$ mv data6 data.tar
$ tar -xf data.tar
$ mv data8.bin data.gz
$ gunzip data.gz
```

## Level 14
password - MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Used -i to use specified file as private key to log in,then use cat to extract the password.
```bash
$ ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
$ cat /etc/bandit_pass/bandit14
```

## Level 15
password - 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
used nc to connect to local host from port 30000.
```bash 
$ nc localhost 30000
```