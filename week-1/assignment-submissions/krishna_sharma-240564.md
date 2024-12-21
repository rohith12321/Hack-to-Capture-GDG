
# writeup 
writeup of bandit till level 15



## Level 0

$ ssh bandit0@bandit.labs.overthewire.org -p 2220 

login as bandit0

password is bandit0

## Level 1

$ ls 

$ cat ./-

## Level 2

$ ls

$ cat spaces\ in \ this\ filename

## Level 3

$ ls

$ cd inhere

$ ls

$ cat .hidden

## Level 4

$ ls

$ cd inhere

$ find . -type f | xargs file

$ cat ./-file07

## Level 5
$ ls

$ cd inhere

$ find . -type f -size 1033c ! -executable

$ cat ./maybehere07/.file2

## Level 6
$ ls

$ find / -type f -user bandit7 -group bandit6 -size 33c

$ cat /var/lib/dpkg/info/bandit7.password

## Level 7
$ ls

$ cat data.txt

$ strings data.txt| grep "millionth"

## Level 8
$ ls

$ cat data.txt

$ sort data.txt | uniq -c

## Level 9
$ ls

$ strings  data.txt | grep "="

## Level 10
$ ls

$ cat data.txt

$ cat data.txt | base64 -d

## Level 11
$ ls

$ cat data.txt

( used cyberchef to resolve rot13 )

## Level 12
$ ls

$ cat data.txt

$ mkdir /tmp/k189

$ cd /tmp/k189

$ ls

$ xxd -r data.txt > data

$ file data

$ mv data file01.gz

$ gzip -d file01.gz

$ file file01

$ mv file01 file02.bz2 

$ bzip2 -d file02.bz2

$ file file02

$ mv file02 file01.gz

$ gzip -d file01.gz

$ file file01

$ mv file01 file.tar

$ tar xf file.tar

$ ls

$ file data5.bin

$ mv data5.bin data.tar

$ tar xf data.tar

$ ls

$ file data6.bin

$  mv data6.bin data.bz2

$ bzip2 -d data.bz2

$ ls

$ file data

$ mv data data.tar

$ tar xf data.tar

$ ls 

$ file data8.bin

$ mv data8.bin data.gz

$ gzip -d data.gz

$ ls

$ file data

$ cat data

## Level 13
$ ls

$ ssh -i sshkey.private bandit14@localhost


$ cat /etc/bandit_pass/bandit14

## Level 14
$ nc localhost 30000

( enter previous password )

## Level 15

$ cat /etc/bandit_pass/bandit15

( password )

$ ncat --ssl localhost 30001

(enter password)

