# Writeup

## Level 0


Using ssh command to connect to the host on port 2220 with username bandit0. 
```bash
  ssh -p 2220 bandit0@bandit.labs.overthewire.org
```
Received an output showing an image of the BANDIT logo and requested password.

Entered password.

## Level 1

Read the contents of the readme file in the home directory using cat command and copied the password onto the clipboard.

```bash
  cat readme
```
Opened a new tab which took me to my local system. Navigated to desktop and created a new file named password and stored my password in it along with the level heading.
```bash
  cd ~/Desktop
  cat > assignment.txt
  Level1 - ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```
```bash
  ssh -p 2220 bandit1@bandit.labs.overthewire.org
```
Entered password.  

## Level 2

Reading the article about the dashed filename alerted me that I cannot just use cat - to view the filename.
So I used the method of writing the pathname to access the file.

```bash
  cat ./-
```
This gave me the password.

Again went to my local system and appended level 2 and password into my file.
```bash
  cd ~/Desktop
  cat >> assignment.txt
  Level2 - 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

```bash
  ssh -p 2220 bandit2@bandit.labs.overthewire.org
```
Entered password.

## Level 3

Filenames with spaces in them are accessed using quotes.

```bash
  cat 'spaces in this filename'
```
Appended the password into my file.
```bash
  cd ~/Desktop
  cat >> assignment.txt
  Level3 - MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
```bash
  ssh -p 2220 bandit3@bandit.labs.overthewire.org
```
Entered password.

## Level 4

Accessed the inhere directory using cd and then viewed the hidden files using ls -a and cat.

```bash
  cd ./inhere
  ls -a
  cat ...Hiding-From-You
```
Appended the password into my file.
```bash
  cd ~/Desktop
  cat >> assignment.txt
  Level4 - 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

```bash
  ssh -p 2220 bandit4@bandit.labs.overthewire.org
```
Entered password.

## Level 5

Checked all the file types using the file and * commands and opened the file which had ASCII Text content.
```bash
  cd ./inhere
  file ./*
  cat ./-file07
```
Appended the password into my file.
```bash
  cd ~/Desktop
  cat >> assignment.txt
  Level5 - 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

```bash
  ssh -p 2220 bandit5@bandit.labs.overthewire.org
```
Entered password.

## Level 6

Printed out all the files recursively with their details in long form and manually checked for the file which has size 1033 bytes and is not executable.
```bash
  cd ./inhere
  ls -aRl
  cat ./maybehere19/.file2
```
Appended the password into my file.
```bash
  cd ~/Desktop
  cat >> assignment.txt
  Level6 - HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```
```bash
  exit
  ssh -p 2220 bandit6@bandit.labs.overthewire.org
```
Entered password.

## Level 7

Used the find command to check for all the files having user, group and size as specified. 
```bash
  find / -group bandit6 -user bandit7 -size 33
  cat /var/lib/dpkg/info/bandit7.password
```
On navigating through these files, found 1 file whose permission wasn't denied and it's name was bandit7 password.

Appended the password into my file.

```bash
  exit
  ssh -p 2220 bandit7@bandit.labs.overthewire.org
```

Entered password.

## Level 8

Searched for the word millionth in the file using grep and by redirecting stdout.
```bash
  cat data.txt | grep "millionth"
```
Copied the text next to it, appended to my file and entered it.
```bash
  exit
  ssh -p 2220 bandit8@bandit.labs.overthewire.org
```

## Level 9

Used a combination of redirection of stdin, uniq and sort commands to find the only line which has count of 1 manually.
```bash
  cat data.txt | sort | uniq -c
```
Copied the text next to it, appended to my file and entered it.

```bash
  exit
  ssh -p 2220 bandit9@bandit.labs.overthewire.org
```

## Level 10

Used the strings command to extract all human readable strings and piped output to search for '==*'
```bash
  strings data.txt | grep '==*'
```
Found the password, appended to my file and entered it.

```bash
  exit
  ssh -p 2220 bandit10@bandit.labs.overthewire.org
```

## Level 11

Converted the base64 using the base64 and decode commands by reading from file using <.
```bash
  base64 --decode < data.txt
```
Found the password, appended to my file and entered it.

```bash
  exit
  ssh -p 2220 bandit11@bandit.labs.overthewire.org
```

## Level 12

Read the document given in the level description and figured that the tr command is used and that we have to specify how to do the encryption for it to decode.
```bash
  tr 'A-Za-z' 'N-ZA-Mn-za-m'< data.txt
```
Found the password, appended to my file and entered it.

```bash
  exit
  ssh -p 2220 bandit12@bandit.labs.overthewire.org
```

## Level 13

Created the directory in the tmp directory as instructed, copied using cp and renamed to new.txt using mv.
```bash
  mkdir /tmp/bruhlol
  cd /tmp/bruhlol
  cp ~/data.txt /tmp/bruhlol
  mv data.txt new.txt
```
Converted hexdump to binary using xxd -r and then checked the file type using file. Identified it as gzip compressed data, so moved it to a zip file and then expanded it.
```bash
  xxd -r new.txt new2.txt
  file new2.txt
  mv new2.txt new2.gz
  gzip -d new2.gz
```
On checking this file, it is still compressed. So checked the file type using file. Identified it as bzip2 compressed data, so moved it to it's zip file type and then expanded it.
```bash
  ls
  cat new2
  file new2
  mv new2 new2.bz2
  bzip2 -d new2.bz2
``` 
Repeating again.
```bash
  ls
  cat new2
  file new2
  mv new2 new2.gz
  gzip -d new2.gz
  ls
  cat new2
  file new2
```
Here, found that the filetype is an archive.
```bash
  mv new2 new2.tar
  tar -xf new2.tar
  ls
```
There is a newfile data5.bin. Repeating our process.
```bash
  file data5.bin
  mv data5.bin data5.tar
  tar -xf data5.tar
  ls
  file data6.bin
  mv data6.bin data6.bz2
  bzip2 -d data6.bz2
  file data6
  mv data6 data6.tar
  mv data6.gz data6.bz2
  bzip2 -d data6.bz2
  ls
  file data8.bin
  mv data8.bin data8.gz
  gzip -d data8.gz
  ls
  file data8
```
Finally the data is in ASCII Text.
```bash
  cat data8
```
Found the password, appended to my file and entered it.  

```bash
  exit
  ssh -p 2220 bandit13@bandit.labs.overthewire.org
```

## Level 14

```bash
  ls
  file sshkey.private
```
Saw that there was a file named sshkey.private with type as private key. Now that we have the private key with us and the authentication is done by verifying whether the user has the private key.

So I use the -i flag to use the private key and login as bandit14. The host is localhost this time and not bandit.labs.overthewire.org, so I entered that. Username - bandit14.

Logged in as bandit 14 and accessed the file to get the password.
```bash
  ssh -i sshkey.private -p 2220 bandit14@localhost
  cat /etc/bandit_pass/bandit14
```
Appended password to my file.

Entered password and logged in.

```bash
  exit
  exit
  ssh -p 2220 bandit14@bandit.labs.overthewire.org
```
## Level 15

Figured out that nc, telnet and the openssl s_client commands are used to establish a connection with a port when on a local host.

```bash
  nc localhost 30000
  MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

Received the final password and entered it to login.

```bash
  exit
  ssh -p 2220 bandit15@bandit.labs.overthewire.org
```
