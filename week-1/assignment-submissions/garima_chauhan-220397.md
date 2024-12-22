# Writeup

## Level 0 
<details> 
  <summary>password:</summary> 

   bandit0
</details>

Using `ssh` command to connect to the host on port 2220 with username bandit0. 
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0
```

Then used `cat` command to display the contents of the readme to get the password.
```bash
$ cat readme
```

## Level 1
<details> 
  <summary>password:</summary> 
  
   ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
</details>

Doing `cat -` was giving error (No such file or directory) so referred to the helpful readings and did the following as suggested
```bash
$ ls
$ cat ./-
```
## Level 2
<details> 
  <summary>password:</summary> 
  
   263JGJPfgU6LtdEvgfWU1XP5yac29mFx
</details>
This seemed natural.

```bash
$ ls
$ cat 'spaces in this filename'
```
An alternate could be `cat spaces\ in\ this\ filename`

## Level 3
<details> 
  <summary>password:</summary> 
  
   MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
</details>

Referred the man page of ls using `man ls` to identify the correct flag to show hidden files.

```bash
$ ls
$ cd inhere
$ ls -a
$ cat ...Hiding-From-You
```
## Level 4
<details> 
  <summary>password:</summary> 
  
   2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
</details>

Used the `file` command to find out the type of each file in the current directory.

```bash
$ ls
$ cd inhere
$ file ./*
$ cat ./-file07
```

## Level 5
<details> 
  <summary>password:</summary> 
  
   4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
</details>

Referred the man page of `find` to get the flags for checking if file is not executable and has a certain size. Then used `file` to find out whether the file was human readable.

```bash
$ ls
$ cd inhere
$ find  ! -executable -size 1033c
$ file ./maybehere07/.file2
$ cat ./maybehere07/.file2
```

## Level 6
<details> 
  <summary>password:</summary> 
  
   HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
</details>

Since it was mentioned anywhere on the server hence went to `\` and then tried to find the file owned by a user, group and of a certain size using relevant flags.

```bash
$ cd ..
$ cd ..
$ ls
$ find -user bandit7 -group bandit6 -size 33c
$ cat ./var/lib/dpkg/info/bandit7.password
```
## Level 7
<details> 
  <summary>password:</summary> 
  
   morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
</details>

Referred to man pages of suggested commands

```bash
$ ls
$ grep millionth data.txt
```
## Level 8
<details> 
  <summary>password:</summary> 
  
   dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
</details>

Referred to man pages of suggested commands, tried `uniq -c data.txt | grep 1 ` first but then read man page of `uniq` carefully to know that `uniq` only checks adjacent lines to be equal. So we need to `sort`first.
`grep` also found lines with count 10, avoided them.

```bash
$ ls
$ sort data.txt | uniq -c | grep 1
```

## Level 9
<details> 
  <summary>password:</summary> 
  
   4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
</details>

Referred to man pages of suggested commands.

```bash
$ ls
$ strings -a data.txt | grep =
```
## Level 10
<details> 
  <summary>password:</summary> 
  
   FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
</details>

`base64` decoded the readable part of data.txt while ignoring the non base64 encoded part(referred to man page of `base64`)

```bash
$ ls
$ strings data.txt | base64 -di
```
## Level 11
<details> 
  <summary>password:</summary> 
  
   dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
</details>

Was not able to figure out by just reading man pages, so searched for Caeser Cipher in bash, that hinted to `tr` so tried reading man page again and `tr 'a-z' 'n-m'` then got the error that 'n-m' is in reverse order. Searched now for ROT13 in bash and got the following:
https://stackoverflow.com/questions/6441260/how-to-shift-each-letter-of-the-string-by-a-given-number-of-letters


```bash
$ ls
$ cat data.txt | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'
```

## Level 12
<details> 
  <summary>password:</summary> 
  
   7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
</details>

Just kept uncompressing and uncompressing(going to different directory was a hint). Also used `xxd` to reverse the hexdump.

```bash
$ dir_name=$(mktemp -d) 
$ cp data.txt $dir_name
$ cd $dir_name
$ file data.txt # got ASCII
$ xxd -r data.txt > data2.bin
$ file data2.bin
$ mv data2.bin data2.gz && gunzip data2.gz
$ ls
$ file data2
$ bunzip2 data2
$ file data2.out
$ mv data2.out data3.gz && gunzip data3.gz
$ ls
$ file data3
$ tar -x -f data3
$ ls
$ file data5.bin
$ tar -x -f data5.bin
$ ls
$ file data6.bin
$ bunzip2 data6.bin
$ file data6.bin.out
$ tar -xf data6.bin.out
$ file data8.bin
$ mv data8.bin data8.gz && gunzip data8.gz
$ file data8
$ cat data8
```
## Level 13
<details> 
  <summary>password:</summary> 
  
   FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
</details>

First tried reading `/etc/bandit_pass/bandit14` as bandit13 itself(that clearly didn't work `:)` ). 
Could not understand man page of `ssh` very well so googled and got:
https://unix.stackexchange.com/questions/23291/how-to-ssh-to-remote-server-using-a-private-key

and then did  `cd /etc/bandit_pass/`
and then `cat bandit14` to get the password

```bash
$ ls
$ ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
$ cd /etc/bandit_pass/
$ cat bandit14
```

## Level 14
<details> 
  <summary>password:</summary> 
  
   MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
</details>

Referred to man page of suggested commands.

```bash
$ cat /etc/bandit_pass/bandit14 | nc 127.0.0.1 30000
```

## Level 15
<details> 
  <summary>password:</summary> 
  
   8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
</details>