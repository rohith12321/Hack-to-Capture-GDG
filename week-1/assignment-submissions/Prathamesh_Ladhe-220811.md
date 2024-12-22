# Writeup

## Level 0


Using ssh command to connect to the host on port 2220 with username and password bandit0. 
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0
```

## Level 1
```bash
$ cat readme
```

```
Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

## Level 2
To read the file named - 
```bash
cat ./-
```
```
Password:263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

## Level 3
```bash 
cat spaces\ in\ this\ filename 
```


After typing s , hit tab for options to autocomplete.
```
Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
## Level 4
```bash 
cd inhere 
ls -la
cat ...Hiding-From-You
```
```
Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

## Level 5
```bash
cd inhere
// (Human Readable -> ASCII)
file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
cat ./-file07
```
```
Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

## Level 6
Using the space command "du"
search for a file with space 1033 bytes
```bash
du -b -a | grep 1033
```
only one file is found.
```
Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```
## Level 7
Use file command with given arguments
- -type f (file)
- -user bandit7 (user)
- -group bandit6 (group)
- -size 33c (size)
```bash
find / -type f -user bandit7 -group bandit6 -size 33c
```
```
Password:morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
## Level 8
grep prints all the instances of millionth
But in this problem, only 1 example is found.
```bash
cat data.txt | grep 'millionth'
```
```
Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```
## Level 9
First tried doing 
```bash
uniq -u data.txt
```
,
but then released the mistake,instead used 
```bash
sort data.txt | uniq -u
```
```
Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
## Level 10
```bash
strings data.txt
```
```
Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
## Level 11
data.txt was written in BASE64
```bash
$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
```
Password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
## Level 12
String found "Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4"
```python
string = "Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4"
result = ""

for char in string:
    if 'a' <= char <= 'z':
        result += chr(((ord(char) - ord('a') + 13) % 26) + ord('a'))
    elif 'A' <= char <= 'Z':
        result += chr(((ord(char) - ord('A') + 13) % 26) + ord('A'))
    else:
        result += char

result
```

```
Password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```
## Level 13
```bash
cat data.txt
```
- Looks like hexdump
therefore 
- Rename the file
```bash
mv data.txt hexfile
```

- Match the signature at each step
- Repeated compression
- - 1f8b (gzip) -> 425a(bz2) -> 1f8b(gzip) -> 6461(tar) -> 6461(tar) -> 425a(bz2) -> 6461(tar) ->1f8b(gzip) -> 
- Use of commands gzip , bzip2,tar
- The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn 
```
Password: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```
## Level 14
```bash
ls
sshkey.private
cat sshkey.private
```
1) Copy the contents and create a file in your local machine (nano sshkey.private) and paste the key , change the permissions of the file by
```bash 
chmod 600 sshkey.private
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

```
Password: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS (found in next level)
```
## Level 15
- All the passwords are stored in /etc/bandit_pass , cat bandit14 to get the password of bandit14 which is MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
- use this to login to the localhost on port 30000
```bash
$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

```
Password: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```