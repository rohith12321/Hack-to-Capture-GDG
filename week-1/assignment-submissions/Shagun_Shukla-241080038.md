# Writeup

## Level 0


Using ssh command to connect to the host on port 2220 with username bandit0. 
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit0
```

## Level 1
Used ls command to see all files in home directory.

Used cat command to print the contents of readme file.
```bash
$ cat readme
```
Used exit to logout of Level0 server.

Used ssh command to connect to the host on port 2220 with username bandit1 using password ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit1
```

## Level 2
Used ls command to see all files in home directory.

Used cat ./ command to print the contents of - file.
(Just using cat - directly just reads standard input)
```bash
$ cat ./-
```
Used exit to logout of Level1 server.

Used ssh command to connect to the host on port 2220 with username bandit2 using password 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit2
```

## Level 3
Used ls command to see all files in home directory.

Used cat command to print the contents of "spaces in this filename" file.
(Use \ for spaces otherwise each file will be considered different argument.)
```bash
$ cat spaces\ in\ this\ filename
```
Used exit to logout of Level2 server.

Used ssh command to connect to the host on port 2220 with username bandit3 using password MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit3
```

## Level 4
Used ls command to see all files in home directory.

Used cd to change the current directory to inhere directory
```bash
$ cd inhere
```

Used ls-a to see all the hidden files in the inhere directory.
```bash
$ ls -a
```
Used cat \. command to print the contents of "...Hidden-From-You" file.
(Use \. for files starting with dot.)
```bash
$ cat ./...Hiding-From-You
```
Used exit to logout of Level3 server.

Used ssh command to connect to the host on port 2220 with username bandit4 using password 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit4
```

## Level 5
Used ls command to see all files in home directory.

Used cd to change the current directory to inhere directory
```bash
$ cd inhere
```

Used file ./* to see file types of all files in the directory. 
```bash
$ file ./*
```
Used cat \. command to print the contents of "-file07" file.
(It was the only file with type ASCII text.)
```bash
$ cat ./-file07
```
Used exit to logout of Level4 server.

Used ssh command to connect to the host on port 2220 with username bandit5 using password 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit5
```

## Level 6
Used ls command to see all files in home directory.

Used cd to change the current directory to inhere directory
```bash
$ cd inhere
```

Used find to check for non executable files of size 1033 bytes as given in question.
```bash
$ find . -size 1033c ! -executable
```
Used cat \. command to print the contents of ".file2" file.
(It was the only file with type ASCII text.)
```bash
$ cat ./.file2
```
Used exit to logout of Level5 server.

Used ssh command to connect to the host on port 2220 with username bandit6 using password HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit6
```
## Level 7

Used find command to search for files owned by user bandit7 and group bandit6 and of size 33 bytes.
```bash
$ find / -user bandit7 -group bandit6 -size 33c -type f
```

A file named bandit7.password appeared among error messages, used cat to open it.
```bash
$ cat /var/lib/dpkg/info/bandit7.password
```
Used exit to logout of Level6 server.

Used ssh command to connect to the host on port 2220 with username bandit7 using password morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit7
```
## Level 8

Used grep command to search for line with 'millionth' in data.txt.
```bash
$ grep millionth data.txt
```

Used exit to logout of Level7 server.

Used ssh command to connect to the host on port 2220 with username bandit8 using password dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit8
```

## Level 9

Used uniq command to print unique lines in data.txt.
(Used sort since data needs to be sorted to use uniq)
```bash
$ sort data.txt | uniq -u
```

Used exit to logout of Level8 server.

Used ssh command to connect to the host on port 2220 with username bandit9 using password 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit9
```

## Level 10

Used a combination of strings commannd to print printable characters and grep command to match lines starting with ===.

```bash
$ strings data.txt | grep ===
```

Used exit to logout of Level9 server.

Used ssh command to connect to the host on port 2220 with username bandit10 using password FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit10
```

## Level 11

Used base64 to decode data.txt

```bash
$ base64 -d data.txt
```

Used exit to logout of Level10 server.

Used ssh command to connect to the host on port 2220 with username bandit11 using password FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit11
```

## Level 12

Used tr command to rotate the letters back from Rot13 in data.txt.

```bash
$ cat data.txt | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'
```

Used exit to logout of Level11 server.

Used ssh command to connect to the host on port 2220 with username bandit12 using password 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit12
```

## Level 13

Used mktemp -d to make a new directory under \tmp.

```bash
$  mktemp -d
```
( The directory made was \tmp\tmp.OmwTZsK80M)

Used cp to copy data.txt in the new directory.

```bash
$  cp -t /tmp/tmp.OmwTZsK80M data.txt
```

Used cd to change the directory to the newly made \tmp\tmp.OmwTZsK80M.

```bash
$  cd \tmp\tmp.OmwTZsK80M
```

Used mv to rename data.txt to copy and remove .txt extension.

```bash
$  mv data.txt copy
```

Used xxd to change the hexdump to binary.

```bash
$  xxd -r copy > binary
```
A file named binary was created. Checked the file type of binary and it turned out to be gzip compressed file.
Renamed binary to binary.gz and decompressed it using gzip.

```bash
$  file binary
$  mv binary binary.gz
$  gunzip binary.gz

```
A file named binary was created. Checked the file type of binary and it turned out to be bzip2 compressed file.
Decompressed it using bzip2.

```bash
$  file binary
$  bzip2 -d binary

```
A file named binary.out was created. Checked the file type of binary.out and it turned out to be gzip compressed file.
Renamed it and decompressed it using gzip.

```bash
$  file binary.out
$  mv binary.out binary.gz
$  gunzip binary.gz

```
A file named binary was created. Checked the file type of binary and it turned out to be POSIX tar archive (GNU).Used tar to decompress it.

```bash
$  file binary
$  tar -xf binary
```
 A file named data5.bin was created which turned out be tar archive again and so on. The files were compressed using tar, gzip and bzip2.
 Decompressing files continuously we get the final file with file type ASCII text with password in it.

```bash
$  file data5.bin
$  tar -xf data5.bin
$  file data6.bin
$  bzip2 -d data6.bin 
$  file data6.bin.out
$  tar -xf data6.bin.out
$  file data8.bin
$  rm binary
$  mv data8.bin binary
$  file binary
$  mv binary binary.gz
$  gunzip binary.gz
$  file binary
$  cat binary
```
Used exit to logout of Level12 server.

Used ssh command to connect to the host on port 2220 with username bandit13 using password FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit13
```

## Level 14

Used ssh command to connect to server with bandit14 username using private key.

```bash
$ ssh bandit.labs.overthewire.org -l bandit14 -p 2220  -i sshkey.private
```

Changed directory to \etc\bandit_pass and read the file bandit14 as user bandit14.
```bash
$ cd \etc\bandit_pass
$ cat bandit14
```

Used exit to logout of Level14 and level13 server.

Used ssh command to connect to the host on port 2220 with username bandit14 using password MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit14
```

## Level 15

Connected to port 30000 as localhost using netcat with password MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```bash
$ netcat localhost 30000
```
Used exit to logout of Level14 server.

Used ssh command to connect to the host on port 2220 with username bandit15 using password 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```bash
$ ssh bandit.labs.overthewire.org -p 2220 -l bandit15
```



