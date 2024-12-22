# Bandit Wargames

## Level 0


Using ssh command to connect to the host on port 2220 with username bandit0. 
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0
```

## Level 1
We use 
```bash
ls
cat readme
```
to read the readme to get the password ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 2
After using ls and then cat- , we realise that this doesnt work

Then we use 
```
cat ./-
```
to get the password 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 3
To open such files,
```
cat spaces\ in\ this\ filename
```
For the password MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 4
As the file is hidden, we use ls -a inside the directory inhere

```
ls
cd inhere
ls -a
cat .  .. ...Hiding-From-You
```

And get 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ as the password

## Level 5
checking file type of all the files,
```
ls
cd inhere/
ls
file ./*
cat ./-file07
```
This gives that the file07 id of ASCII text and others are data files<br>
Password:4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw


## Level 6
We find that there are many files in the directory, so we use find to satisfy all the conditions
```
dd inhee
find -type f -size 1033c 
cat ./inhere/maybehere07/.file2
```
Password:HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 7

```
find / -type f -user bandit7 -group bandit6 -size 33c
cat /var/lib/dpkg/info/bandit7.password
```
We get a lot of files after using find and one of them is /var/lib/dpkg/info/bandit7.password which gives us
Password:morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj


## Level 8
Finding for the word millionth in the file
```
grep millionth data.txt
```
we get the password:dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
## Level 9
Sort the data and find which text occurs only once
```
sort data.txt | uniq -u
```
PAssword:4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 10
After using 
```
strings data.txt | grep "=="
```
We get ========== the<br>
3JprD========== passwordi<br>
~fDV3========== is<br>
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey<br><br>
Hence, the password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Level 11
We get some base64 data at data.txt. So,
```
cat data.txt | base64 -d
```
gives us the password:dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## Level 12
Transform the data
```
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
Password:7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
## Level 13
```
ls
cd /tmp
mktemp -d
cd/tmp/tmp.1kBCwbgdVr
cp ~/data.txt .
mv data.txt hexdump.txt
mv hexdump.txt hexdump_data
xxd -r hexdump_data compressed_data
file compressed_data (gz file)
mv compressed_data compressed_data.gz
gzip -d compressed_data.gz
file compressed_data
mv compressed_data compressed_data.bz2
bzip2 -d compressed_data.bz2
file compressed_data
mv compressed_data compressed_data.gz
gzip -d compressed_data.gz
file compressed_data
mv compressed_data compressed_data.tar
tar -xf compressed_data.tar
ls
file data5.bin
tar -xf data5.bin
ls
file data6.bin
bzip2 -d data6.bin
ls
file data8.bin
mv data8.bin data8.gz
gzip -d data8.gz
cat data8
```
Finally we get the password:FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## Level 14
while in bandit13 look for sshkey.private
```
ls
exit
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private . 
ls -la
chmod 700 sshkey.private 
ls -la
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```
This will give direct access to bandit14
## Level 15
While in bandit 14 access the password in /etc/bandit_pass/bandit14
```
cd ..
cd ..
cat /etc/bandit_pass/bandit14
```
This will give the password MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS to enter in
```
nc localhost 30000
```
Password:8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
