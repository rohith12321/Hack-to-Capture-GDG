# Level 0
Run `ssh -p 2220 bandit0@bandit.labs.overthewire.org`. You'll get a prompt asking for a password, enter `bandit0` as instructed.

# Level 1
`ls` gives you:
```
readme
```
`cat readme` gives:
```
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```
The password for `bandit1` is `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

# Level 2
Just like before, `ls` gives you
```
-
```
If we run `cat -`, it expects an input. `-` as an argument refers to stdin and therefore we'll have to run `cat ./-` (the `./` just means that it's a file in the current directory).
This gives us the password for `bandit2`: `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

# Level 3
Since the filename has whitespaces, we surround the filename with double (or single) quotes.
Running `cat "spaces in this filename"` gives us the password for `bandit3`: `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

# Level 4

We cd into `inhere` by running `cd inhere`. Since the file is hidden, we run `ls -a`and we see a file named `...Hiding-From-You`. This gives us the password for `bandit4`: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

# Level 5

cd into `inhere` and see the output of cat for each file inside the directory. `-file07` contains the password for `bandit5`: `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

# Level 6

cd into `inhere`. We see that `inhere` contains multiple folders. We run `ls -laR` (we need the recursive option since these folders themselves contain multiple files/folders)
The long list option allows us to see file permissions and size in bytes. We need files that don't have an x (for executable). To do this, we pipe the output of ls to a grep command: `ls -laR | grep -v x` (the `-v` flag inverts matches since we want lines that don't have a x). At this point it's pretty easy to see (with another grep) that `~/inhere/maybehere07/.file2` is the only file that fits the last two properties. This gives us the password for `bandit6`: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

# Level 7

This time we don't know where the password is stored but we do know it's somewhere on the server. Hence we search the root directory (`/`) using `find`. We run `find / -user bandit7 -group bandit6` but since a lot of files are read protected, we'll get a lot of "Permission denied" errors so we redirect stderr to `/dev/null` (virtual folder that acts like a sink and any data redirected to it just disappears). Running `find / -user bandit7 -group bandit6 2>/dev/null` gives us
```
/var/lib/dpkg/info/bandit7.password
```
which gives us the password for `bandit7`: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

# Level 8

cat `data.txt` and pipe its output to grep searching for "millionth". Running `cat data.txt | grep millionth` we get a match: `millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`. This gives us the password for `bandit8`: `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

# Level 9

This is exactly what the `-u` flag does in `uniq` but this won't be enough. If we run `uniq --help`, a note reads: "'uniq' does not detect repeated lines unless they are adjacent". Thus, we sort the file first and then pipe that to `uniq -u`. Running `sort data.txt | uniq -u` we get the password for `bandit9`: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

# Level 10

Get human-readable text using `strings`. This gives `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey` as the password for `bandit10`

# Level 11

Run `base64 --decode data.txt`. This gives you the password for `bandit11`: `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`
# Level 12

```python
from string import ascii_lowercase, ascii_uppercase

def rot13(s): return s[13:]+s[:13]

print(ascii_lowercase + ascii_uppercase, rot13(ascii_lowercase) + rot13(ascii_uppercase))
```
The above python script gives you a string for tr replacement.
Now run `cat data.txt | tr <the output you got from running the script>`
This gives you: `The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4` suggesting that the password for `bandit12` is `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`.
# Level 13

Because of the way file/directory permissions have been set in this folder, we'll have to work in a directory inside `/tmp`. To create a temporary directory here, we use `mktemp -d` and we cd into it. We copy the `data.txt` file by running `cp ~/data.txt .`.
It's given that this file is a hexdump so we use `xxd` along with the revert flag.
Run `xxd -r data.txt > compressed`. To view the compressed file (`compressed` in this case), we use `hexdump compressed`. The first few bytes will give us the file signature (which lets us know what compression format/algorithm was used). 
We refer to a [list of file signatures](https://en.wikipedia.org/wiki/List_of_file_signatures) and see that a hex signature of `1F 8B` is used for a gzip file (the hexdump shows `8b1f` but that's because of endianness I think).
Decompress this file by running `mv compressed compressed.gz && gzip -d compressed.gz`. We now get a new file (with the same base name). Again, run `hexdump compressed`. This time the file signature matches with a bzip2 file (`42 5A 68`). Decompress this file by running `mv compressed compressed.bz2 && bzip2 -d compressed.bz2`. Repeat the same step again (the next time it's a gzip file). Running `hexdump compressed` gives us a signature that's not in the list. It could be an archive, so we run `tar -xf compressed` instead and we get a `data5.bin` this time. We see the same signature appearing again so we run `tar -xf data5.bin` and we get a `data6.bin` which is a bzip2 file so we run `mv data6.bin data6.bz2 && bzip2 -d data6.bz2`. We get another archive -> `tar -xf data6` -> `data8.bin` which is a gzip file -> `mv data8.bin data8.gz && gzip -d data8.gz` -> `data8` which finally contains the password for `bandit13`: `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

# Level 14

We see that there is a `sshkey.private` file in the home directory. On our local machine, we run `scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private .` To login with `bandit14`, we supply the private key while using the `-i` flag. While in the same working directory, we run `ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org` but this gives us an error:
```
Permissions 0640 for 'sshkey.private' are too open.
It is required that your private key files are NOT accessible by others.
```
So we give read permissions to ONLY the owner of the file by running `chmod 400 sshkey.private` and then we connect to the server successfully.

# Level 15

The password for the current user according to the problem statement given previously is located at `/etc/bandit_pass/bandit14` this gives us the password for `bandit14`: `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`. We use `nc` (used to read/write data over a connection) to submit this password to `localhost`. Run `nc localhost 30000` and input the password we just got, we get a message saying "Correct!" followed by the password for `bandit15`: `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`.

# Level 16

Quoting the man page of `openssl`:
```
s_client
           This  implements  a  generic SSL/TLS client which can establish a transparent connection to a remote server speaking SSL/TLS. It's intended for testing  purposes  only  and  provides  only  rudimentary interface functionality but internally uses mostly all functionality of the OpenSSL ssl library.
```
This is exactly what we need so we connect to localhost over port number 30001 by running `openssl s_client -connect localhost:30001`. We get a bunch of information about authentication certificates, handshakes, etc. but all we need to do is input the password we got after completing the previous l | evel. This gives us the password for `bandit16`: `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`. 

# Level 17

We use the `nmap` command. Under the "SERVICE AND VERSION DETECTION" section in the man page of `nmap` we see that the flag used for version detection is `-sV` and port ranges are specified using the `-p` flag so we run `nmap -sV localhost -p 31000-32000` and get the following output:
```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-12-22 12:14 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00010s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
(...)
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 157.93 seconds
```
This kept giving me "KEYUPDATE" so I had to use the `-ign_eof` flag (stands for ignore EOF). Port 31518 just gave back the same password so I tried the other port, port 31790 which gave me a RSA private key for presumably the next ssh login.

```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

# Level 18

We log into `bandit17` using the private key we just got by completing the previous level.
To see the difference between `passwords.old` and `passwords.new` we use the `diff` command. This gives us:
```
42c42
< ktfgBvpMzWKR5ENj26IbLGSblgUG9CzB
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```
The man page for `diff` tells us what the angle brackets mean. < represent lines from FILE1 (the first argument) and > represent lines from FILE2 (second argument). Since the problem states that the password for the next level is in `passwords.new`, the password for `bandit18` is `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

# Level 19

Similar to what we did in level 14, we use `scp` to copy `readme` located at `/home/bandit18/readme` to our local machine by running `scp -P 2220 bandit18@bandit.labs.overthewire.org:/home/bandit18/readme .` and entering in the password we got by solving the last level when prompted. We can now simply run `cat readme` on our local machine to obtain the password for `bandit19`: `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

# Level 20

Running `ls -la` in the home directory we see that `bandit20-do` is an executable. Running it without any arguments we get the following:
```
Run a command as another user.
  Example: ./bandit20-do id
```
Running `ls -la` in the given `/etc/bandit_pass` directory, we see that `bandit20` is owned by `bandit20` with read privileges to the owner and since the binary given to us can run commands as `bandit20`, we can simply run `./bandit20-do /etc/bandit_pass/bandit20` to get the password for `bandit20` as `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`