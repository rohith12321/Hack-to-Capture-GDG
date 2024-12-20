# Bandit Wargame
# Writeup 

## LEVEL 0
Using the cat command to read the file “readme”.
```bash
bandit0@bandit:~$ cat readme
```
```bash
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 1
Since the file name contains -, directly writing file name after – implies starting of an option of cat command which is not the case. Hence, we have to write ./-  instead of simply -.
```bash
bandit1@bandit:~$ cat ./-
```
```bash
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 2
Since there are spaces in the file name, file name has to be enclosed within double quotes before it can be executed with the command.
```bash
bandit2@bandit:~$ cat "spaces in this filename"
```
```bash
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 3
The password file is hidden and inside the directory inhere. Hence after changing the directory uing cd command, ls -a is used to view the names of all files including the hidden ones. Then, the contents of the file are printed using the cat command.
```bash
bandit3@bandit:~$ ls
```
```bash
inhere
```
```bash
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls

bandit3@bandit:~/inhere$ ls -a
```
```bash
.  ..  ...Hiding-From-You
```
```bash
bandit3@bandit:~/inhere$ cat .  ..  ...Hiding-From-You
```
```bash
cat: .: Is a directory
cat: ..: Is a directory
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 4
After searching the file type of each file manually using file command.  Then printed the contents of the file containing ASCII text using the cat command.
```bash
Ls
```
```bash
Inhere
```
```bash
cd inhere
ls
```
```bash
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
```
```bash
bandit4@bandit:~/inhere$ file ./-file01
```
```bash
./-file01: data
```
```bash
bandit4@bandit:~/inhere$ file ./-file02
```
```bash
./-file02: data
```
```bash
bandit4@bandit:~/inhere$ file ./-file03
```
```bash
./-file03: data
```
```bash
bandit4@bandit:~/inhere$ file ./-file04
```
```bash
./-file04: data
```
```bash
bandit4@bandit:~/inhere$ file ./-file05
```
```bash
./-file05: data
```
```bash
bandit4@bandit:~/inhere$ file ./-file06
```
```bash
./-file06: data
```
```bash
bandit4@bandit:~/inhere$ file ./-file07
```
```bash
./-file07: ASCII text
```
```bash
bandit4@bandit:~/inhere$ file ./-file08
```
```bash
./-file08: data
```
```bash
bandit4@bandit:~/inhere$ file ./-file09
```
```bash
./-file09: data

```
```bash
bandit4@bandit:~/inhere$ cat ./-file07
```
```bash
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL5
Finding the file using file command down the current directory (represented using .) after specifying the options: readable, size as 1033 bytes and non-executable respectively. Then used the file path got from above command to print the contents of the file using cat command.

```bash
bandit5@bandit:~$ find . -readable -size 1033c ! -executable
```
```bash
./inhere/maybehere07/.file2
```
```bash
bandit5@bandit:~$ cd inhere/maybehere07
bandit5@bandit:~/inhere/maybehere07$ cat .file2
```
```bash
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 6
Finding the file using file command down the current directory (represented using .) after specifying the options: username as bandit7, group name as bandit 6 and size as 33 bytes. Then used the file path got from above command to print the contents of the file using cat command.

```bash
bandit6@bandit:~$ find / -size 33c -user bandit7 -group bandit6
```
```bash
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
```
```bash
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 7
Used grep command to print the portion of the file data.txt having pattern like the word millionth followed by some other words. The text succeeding the word “millionth” is the password.
```bash
bandit7@bandit:~$ grep "millionth" data.txt
```
```bash
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 8
Sort command sorts the lines in data.txt file in ascending. The output is then piped to uniq command which prints only those lines in the code that have occurred just once.
```bash
bandit8@bandit:~$ sort data.txt | uniq -u
```
```bash
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 9
Strings command is used to print the human readable characters in data.txt. Then, the output is manually searched for the password.
```bash
bandit9@bandit:~$ strings data.txt 
```
```bash
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 10
The base64 encoded data is first read from data.txt and then piped to “base64 –decode” for converting it into ASCII text.
```bash
bandit10@bandit:~$ cat data.txt | base64 --decode
```
```bash
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 11
tr command translates the characters in the output of the file backwards as specified within the quotes. In this case, it is translated by 13 places.

```bash
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
```bash
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 12
The original file is a hexdump and has been formed after several compressions. First made a separate folder under tmp and copied the file here. Will perform all the decompressions and extractions here.
```bash
bandit12@bandit:~$ mkdir /tmp/folder1
bandit12@bandit:~$ cp data.txt /tmp/folder1
bandit12@bandit:~$ cd /tmp/folder1
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data.txt
```
Reversing the process by which hexdump was formed.
```bash
bandit12@bandit:/tmp/folder1$ xxd -r data.txt > data
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data  data.txt
```
Checking the file type of data formed after reversing hexdump.
```bash
bandit12@bandit:/tmp/folder1$ file data
```
```bash
data: gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 574
```
Changing the file extension to .gz so that it can be decompressed using gzip -d.
```bash
bandit12@bandit:/tmp/folder1$ mv data file.gz
bandit12@bandit:/tmp/folder1$ gzip -d file.gz
```
The resultant file is bzip2 compressed.
```bash
bandit12@bandit:/tmp/folder1$ file file
```
```bash
file: bzip2 compressed data, block size = 900k
```
Changing the extension of the file to .bz2 so that it can be decompressed using bzip2 -d.
```bash
bandit12@bandit:/tmp/folder1$ mv file file.bz2
bandit12@bandit:/tmp/folder1$ bzip2 -d file.bz2
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data.txt  file
```
The resultant file is gzip compressed. Again changing the extension followed by decompression.
```bash
bandit12@bandit:/tmp/folder1$ file file
```
```bash
file: gzip compressed data, was "data4.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 20480
```
```bash
bandit12@bandit:/tmp/folder1$ mv file file.gz
bandit12@bandit:/tmp/folder1$ gzip -d file.gz
```
The resultant file is tar archived. Extracting it after changing the extension to .tar and extracting it.
```bash
bandit12@bandit:/tmp/folder1$ file file
```
```bash
file: POSIX tar archive (GNU)
```
```bash
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data.txt  file
```
```bash
bandit12@bandit:/tmp/folder1$ mv file file.tar
bandit12@bandit:/tmp/folder1$ tar xf file.tar
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data5.bin  data.txt  file.tar
```
The resultant file is tar archived. Extracting it after changing the extension to .tar and extracting it.
```bash
bandit12@bandit:/tmp/folder1$ file data5.bin
```
```bash
data5.bin: POSIX tar archive (GNU)
```
```bash
bandit12@bandit:/tmp/folder1$ rm file.tar
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data5.bin  data.txt
```
```bash
bandit12@bandit:/tmp/folder1$ mv data5.bin data5.tar
bandit12@bandit:/tmp/folder1$ tar xf data5.tar
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data5.tar  data6.bin  data.txt
```
The resultant file is bzip2 compressed. Decompressing it further.
```bash
bandit12@bandit:/tmp/folder1$ file data6.bin
```
```bash
data6.bin: bzip2 compressed data, block size = 900k
```
```bash
bandit12@bandit:/tmp/folder1$ rm data5.tar
bandit12@bandit:/tmp/folder1$ mv data6.bin data6.bz2
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data6.bz2  data.txt
```
```bash
bandit12@bandit:/tmp/folder1$ bzip2 -d data6.bz2
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data6  data.txt
```
The resultant file is tar archived. Extracting it after changing the extension to .tar and extracting it.
```bash
bandit12@bandit:/tmp/folder1$ file data6
```
```bash
data6: POSIX tar archive (GNU)
```
```bash
bandit12@bandit:/tmp/folder1$ mv data6 data6.tar
bandit12@bandit:/tmp/folder1$ tar xf data6.tar
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data6.tar  data8.bin  data.txt
```
The resultant file is gzip compressed. Again changing the extension followed by decompression.
```bash
bandit12@bandit:/tmp/folder1$ file data8.bin
```
```bash
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 49
```
```bash
bandit12@bandit:/tmp/folder1$ rm data6.tar
bandit12@bandit:/tmp/folder1$ mv data8.bin data8.gz
bandit12@bandit:/tmp/folder1$ gzip -d data8.gz
bandit12@bandit:/tmp/folder1$ ls
```
```bash
data8  data.txt
```
Finally we get an ASCII text file with password in it.
```bash
bandit12@bandit:/tmp/folder1$ file data8
```
```bash
data8: ASCII text
```
```bash
bandit12@bandit:/tmp/folder1$ cat data8
```
```bash
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 13
Logging in as user bandit14 on machine localhost.
```bash
bandit13@bandit:~$ ssh -l bandit14 localhost -i sshkey.private -p 2220
```
Going to the directory specified in the question and reading the ASCII text file.
```bash
bandit14@bandit:~$ cd /etc/bandit_pass
bandit14@bandit:/etc/bandit_pass$ ls
```
```bash
bandit0  bandit10  bandit12  bandit14  bandit16  bandit18  bandit2   bandit21  bandit23  bandit25  bandit27  bandit29  bandit30  bandit32  bandit4  bandit6  bandit8
bandit1  bandit11  bandit13  bandit15  bandit17  bandit19  bandit20  bandit22  bandit24  bandit26  bandit28  bandit3   bandit31  bandit33  bandit5  bandit7  bandit9
```
```bash
bandit14@bandit:/etc/bandit_pass$ cat bandit14
```
```bash
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 14
Using NetCat to establish a connection to localhost via port 30000. Then, typing in the password of Level 14 and finally getting the password to Level 15.
```bash
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```
```bash
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

<hr style="height: 6px; background-color: black; border: none;" />

## LEVEL 15
Using openssl command to connect to localhost via port 30001.
```bash
openssl s_client -connect localhost:30001
```
```bash
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```
