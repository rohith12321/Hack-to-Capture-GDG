# Writeup

## Level 0


Using ssh command to connect to the host on port 2220 with username bandit0. 
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0
```

## Level 1
had to use cd, ls and less to change directory,view directory and read the readme text file respectively

## Level 2
to read the '-' file, had to use ./-
```bash
$ cat ./-
```
## Level 3
```bash
$ ls "spaces in this filename"
```
## Level 4
had to use ls -a to view the hidden file and then used cat to read it
```bash
$ cat $(ls -a)
```
## Level 5
had to use '--' after cat so that -f was not taken as a function and tried for all the files present to see which one had the human readable text
```bash
$ cat -- -file07
```
## Level 6
none of the visible files was of 1033 bytes so had to check the hidden ones also by doing:
```bash
$ls -l */.* |grep 1033 
```
which gave that .file2 in maybehere07 satisfied the conditions, so had to view the file through:
```bash
$ cat -- maybehere07/.file2
```
## Level 7
to find the file that satisfied the given conditions, used:
```bash
$ find / -user bandit7 -group bandit6 -size 33c 
```
there was only 1 file for which there was permission so read into the file to get the password
```bash
$cat /var/lib/dpkg/info/bandit7.password
```
## Level 8
to search for the word millionth, simply used grep command
```bash
$ data.txt|grep millionth
```
## Level 9
to get the unique line in the data file, used the sort and uniq command
```bash
$sort data.txt|uniq -u
```
## Level 10
on using the strings command, the string of continuous '=' was visible
```bash
$strings data.txt 
```
## Level 11
had to decode the base64 encoded code in the data.txt file
```bash
$ cat data.txt
$ echo "VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg=="|base64 -d
```
## Level 12
had to use tr command to the text in the file to rotate by 13
```bash
$ echo "Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
## Level 13
had to create a temp folder, in which data.txt was moved, reversed the hex dump, and had to use reverse tar gzip and bzip2 several times to get the file with the password, along with using mv whenever a renaming was necessary

## Level 14
to connect using the given ssh key had to do:
```bash
$ ssh -i sshkey.private -p 2220 bandit14@localhost
```
after doing this, had to read into /etc/bandit_pass/bandit14
```bash
$ cat /etc/bandit_pass/bandit14
```
## Level 15
to submit password to port 30000 of local host:
```bash
$ nc localhost 30000
```
