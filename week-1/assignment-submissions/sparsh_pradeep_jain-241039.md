# Writeup

## Level 0


Using ssh command to connect to the host on port 2220 with username bandit0. 
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220 
```
And then typing password on being prompted

## Level 1
Now we look for a file called readme
```bash
$ ls
```
and then
```bash
$ cat readme
```
This gives us the password.
## Level 2
Now we need to access a file named -
so we type
```bash
$ cat ./-
```
This gives us the password.

## Level 3
Next we need to access a filename with spaces in it, so we just put '' around it.
```bash
$ cat ./'spaces in this filename'
```
This gives us the password.
## Level 4
Now we access the inhere directory first using
```bash
$ cd inhere/
```
Then we need to see the hidden file, so we use
```bash
:~/inhere$ ls -a
```
Finally to get the password we do
```bash
$ cat ./...Hiding-From-You
```
This gives us the password.
## Level 5
First we go to the inhere directory
```bash
$ cd inhere/
```
Now we want to check type of all files present in the directory
We can use this command
```bash
$ find . -type f | xargs file
```
We find that file07 is containing ASCII text
So we check its contents and get the password.
```bash
$ cat ./-file07
```
This gives us the password.
## Level 6
Now we need to find a file satisfying a few conditions
First we go to the inhere directory
```bash
$ cd inhere/
```

Now we apply the conditions
```bash
$ find -type f ! -executable -size 1033c
```
Then we access the file contents
```bash
$ cat ./maybehere07/.file2
```
This gives us the password.
## Level 7
Now we need to search the server(/)
```bash
$ find / -type f -user bandit7 -group bandit6 -size 33c
```
We get which file has the password.
```bash
$ cat /var/lib/dpkg/info/bandit7.password
```
This gives us the password.
## Level 8
Now to find a word we use the grep command
```bash
$ strings data.txt | grep "millionth"
```
This gives us the password.
## Level 9
This file has a lot of repeated lines, so we use the uniq function along with sort to find which lines occurs only once
```bash
$ sort data.txt | uniq -c
```
This gives us the password.
## Level 10
Now we need to check the lines containing a bunch of = signs
We use the following command
```bash
$ strings data.txt | grep '=='
```
This gives us the password.
## Level 11
Now the password is encoded in base64 so we use the base64 command to decode it
```bash
$ base64 -d data.txt
```
This gives us the password.
## Level 12
Here the password is Rot13 cipher encoded
First we access it using
```bash
$ cat data.txt
```
Then we go to the Rot13 decoder on dcode.fr and paste the text obtained.
This gives us the password.
## Level 13
First we make a directory under tmp
```bash
$ mkdir /temp/spark
```
Then we copy the file and move to the directory
```bash
$ cp data.txt /tmp/spark
$ cd /tmp
$ cd ./spark
$ ls
```
data.txt is a hexdump so we use xxd command
```bash
$ xxd -r data.txt > data
$ file data
```
This gives a gzip compressed file so we rename and decompress
```bash
$ mv data data.gz
$ gzip -d data.gz
$ file data
```
This gives a bzip2 compressed file so we rename and decompress
```bash
$ mv data data.bz2
$ bzip2 -d data.bz2
$ file data
```
This gives a gzip compressed file so we rename and decompress
```bash
$ mv data data.gz
$ gzip -d data.gz
$ file data
```
This gives a tar archive so we extract that
```bash
$ mv data data.tar
$ tar xf data.tar
$ ls
$ file data5.bin
```
This gives another tar archive, so we extract that
```bash
$ rm data.tar
$ mv data5.bin data.tar
$ tar xf data.tar
$ ls
$ file data6.bin
```
This gives a bzip2 compressed file so we rename and decompress
```bash
$ mv data6.bin data.bz
$ bzip2 -d data.bz
$ ls
$ file data
```
This gives a tar archive so we extract that
```bash
$ rm data.tar
$ mv data data.tar
$ tar xf data.tar
$ ls
$ file data8.bin
```
This gives a gzip compressed file, so we rename and decompress
```bash
$ mv data8.bin data.gz
$ gzip -d data.gz
$ ls
$ file data
```
This finally gives a file with ASCII text so we read that
```bash
$ cat data
```
This gives us the password.
## Level 14
We need to use the private key given using -i
```bash
$ ssh -o HostKeyAlgorithms=ssh-ed25519 -i sshkey.private -p 2220 bandit14@localhost
```
This takes us to the next level.
## Level 15
First we get the password
```bash
$ cat /etc/bandit_pass/bandit14
```
Then we enter the password after the following command
```bash
$ nc localhost 30000
```
This gives us the password. (8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo)