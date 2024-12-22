   # Writeup

---

## Level 0

- using the ssh command to connect to a host using the command
  ```
  ssh bandit0@[port:link] -p 2220 -l bandit0 
  ```

## Level 0 -> 1

- looking into the content of readme file using cat command
  ```
  cat readme
  ```
  The password for the next level : ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1 -> 2

- opening the "dashed file" using the following commannd:
  ```
  cat ./-
  ```
  The password for the next level : 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2 -> 3

- opening the file that contain spaces between it
  ```
  cat "spaces in this filename"
             or
  cat spaces\ in\ this\ filename
  ```
  The password for the next level : MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 3 -> 4

- Going inside the directory "inhere" and then -a to list hidden files
  ```
  cd inhere
  ls -a
  cat ...Hiding-From-You
  ```
  The password for the next level : 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4 -> 5

- using the following command in the home directory to print all the stuff in all the files in the "inhere" directory
  we will get the password in one of the file printed
  ```
  cat $(find ./inhere -iname "*file*") # we will not be reqired to check all the files individually
  ```
  The password for the next level : 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5 -> 6

- using the following command to find a file of a particular size
  ```
  find ./inhere -size 1033c
  ```
- More aproatiate to use *find . -type f -size 1033c ! -executable*

  The password for the next level : HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 6 -> 7

- using the following we will get a file with persmission not denied . May use "2> /dev/null" to avoid error messages
  ```
  find / -user bandit7 -group bandit6 -size 33c
  cat [file]
  find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
  ```
- All the error messages will be moved to /dev/null using the above command to give a better readbility. *USE MAY USE
  THE FOLLOWING TO UPDATE THE FILE WHERE YOU WANT TO STORE YOUR ERROR MESSAGES FOR LATER USE*
  ```
  command 2> errorfile.txt 
  ```
  The password for the next level : morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Level 7 -> 8

- using the grep command to easily get the password
  ```
  grep millionth data.txt
  ```
  The password for the next level : dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 8 -> 9

- using the sort and uniq command we can find the line that occurs only once
  ```
  sort -f data.txt | uniq -u
  ```
  The password for the next level : 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 9 -> 10

- you can use xxd or strings to get the password
  ```
  strings data.txt | grep "===*"
  xxd -c 64 data.txt | grep "===*"
  ```
  The password for the next level : FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Level 10 -> 11

- using the base64 decode command to get the password
  ```
  base64 --decode data.txt
  ```
  The password for the next level : dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## Level 11 -> 12

- using the command for "ROT13" :
  ```
  cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
  ```
  The password for the next level : 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## Level 12 -> 13

```
strings data.txt   #   gives hex dump file
xxd -r data.txt | file -   #  gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max 
                              compression, from Unix (file - is used to output from stdin)
```

- Now decompressing according to the output of next compression file using additional pipe :
  ```
  xxd -r data.txt | zcat |file -    # bzip2 compressed data, block size = 900k

  xxd -r data.txt | zcat |bzcat | file -    # gzip compressed data, was "data4.bin", last modified: Thu Sep 19 07:08:15 
                                              2024, max compression, from Unix

  xxd -r data.txt | zcat |bzcat | zcat | file -  # POSIX tar archive (GNU)
  ```
  The (tar -xO) command in Linux is used to extract the contents of a tar archive and output it directly to the standard
  output.
- Finally doing it further we get at the end :
  ```
  xxd -r data.txt |zcat |bzcat |zcat|tar -xO|tar -xO|bzcat|tar -xO|zcat|file -  # ASCII text

  xxd -r data.txt |zcat |bzcat |zcat|tar -xO|tar -xO|bzcat|tar -xO|zcat
  ```
  The password for the next level : FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## Level 13 -> 14

- after getting the path of private-key use the following and also mention the  port 2220 if you want login in bandit14 directly from bandit13 , if not it will try connecting from port 20 which will give error in login
  ```
  ssh -i /home/bandit13/sshkey.private bandit14@bandit.labs.overthewire.org -p 2220 -l bandit14
  ```
- after login into bandit14 use cat see the password for it:
  ```
  cat /etc/bandit_pass/bandit14
  ```
  The password for the next level : MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

## Level 14 -> 15

- using telnet to connect to the localhost using port 30000
  ```
  telnet localhost 30000
  ```
  The password for the next level : 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo


