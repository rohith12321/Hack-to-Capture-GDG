# Writeup

## Level 0
password: bandit0

Using ssh command to connect to the host on port 2220 with username bandit0. 
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0
```

Then used cat command to display the contents of the readme to get the password.
```bash
$ cat readme
```

## Level 1
password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If


the helpful reading

```bash
$ ls
$ cat ./-
```
## Level 2
password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

```bash
$ ls
$ cat 'spaces in this filename'
```

## Level 3
password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

```bash
$ ls
$ cd inhere
$ ls -a
$ cat ...Hiding-From-You
```
## Level 4
password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

```bash
$ ls
$ cd inhere
$ file ./*
$ cat ./-file07
```

## Level 5
password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

```bash
$ ls
$ cd inhere
$ find  ! -executable -size 1033c
$ file ./maybehere07/.file2
$ cat ./maybehere07/.file2
```
## Level 6
password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG


since server written so should go to /

```bash
$ cd ..
$ cd ..
$ ls
$ find -user bandit7 -group bandit6 -size 33c
$ cat ./var/lib/dpkg/info/bandit7.password
```
## Level 7
password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

```bash
$ ls
$ grep millionth data.txt
```
## Level 8
password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

we need to sort first, grep also found lines with 10

```bash
$ ls
$ sort data.txt | uniq -c | grep 1
```

## Level 9
password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

```bash
$ ls
$ strings -a data.txt | grep =
```
## Level 10
password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

output: The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

```bash
$ ls
$ strings data.txt | base64 -di
```
## Level 11
password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

https://stackoverflow.com/questions/6441260/how-to-shift-each-letter-of-the-string-by-a-given-number-of-letters

output: The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

```bash
$ ls
$ cat data.txt | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'
```

## Level 12
password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
## Level 13
## Level 14
## Level 15