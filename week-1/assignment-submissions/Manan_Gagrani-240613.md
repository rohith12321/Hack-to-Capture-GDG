## Level 0

Use ssh command to connect to the host on port 2220 with username bandit0.


```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```


Password - bandit0

## **Level 0 → Level 1**

Use ls command to see that there is a readme file.


```
ls
```


Use cat command to view the contents of readme.


```
cat readme
```


Password - ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## **Level 1 → Level 2**

Use ls command to see that there is a file called “-”.


```
ls
```


Use cat command while redirecting the input to “-”.


```
cat < -
```


Password - 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## **Level 2 → Level 3**

Use ls command to see that there is a file called “spaces in this filename”.


```
ls
```


Use cat command with double quotes so “spaces in this filename” is treated as one file. 


```
cat "spaces in this filename"
```


Password - MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## **Level 3 → Level 4**

Use ls command to find a folder named inhere.


```
ls
```


Use cd command to navigate to the inhere folder.


```
cd inhere
```


Use ls -a command to show hidden files.


```
ls -a
```


Use cat command to view the contents of ...Hiding-From-You


```
cat ...Hiding-From-You
```


Password - 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## **Level 4 → Level 5**

Use file command to check the type of all files in the directory. We want the one with type: ASCII text.


```
file ./*
```


Use cat command while redirecting the input to “-file07”.


```
cat < -file07
```


Password - 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## **Level 5 → Level 6**

Use find command with the conditions (type: regular files, size: 1033 bytes, not executable)


```
find . -type f -size 1033c ! -executable
```


Since, we only found one file there is no need to check file types.

Use cat command to view the contents of the file.


```
cat ./maybehere07/.file2
```


Password - HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## **Level 6 → Level 7**

Since the file is on the whole server, we use find command with /


```
find / -type f -user bandit7 -group bandit6 -size 33c
```


Use cat command to view the con

Password - morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## **Level 7 → Level 8**

Use ls command to see that there is a data.txt file.


```
ls
```


Use strings command with grep to find the word millionth in data.txt


```
strings data.txt | grep "millionth"
```


Password - dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## **Level 8 → Level 9**

Use sort command with the uniq command to display only unique lines.


```
sort data.txt | uniq -u
```


Password - 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## **Level 9 → Level 10**

Use strings command with grep to find “=” sign and hence the password.


```
strings data.txt | grep =
```


Password - FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## **Level 10 → Level 11**

Use base64 command to decode the password.


```
base64 -d data.txt
```


Password - dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## **Level 11 → Level 12**

Use the following command resolves ROT13 encoded data.


```
cat data.txt | tr a-zA-Z n-za-mN-ZA-M
```


Password - 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## **Level 12 → Level 13**

Use mkdir command to create a directory inside the tmp directory.


```
mkdir /tmp/manan
```


Copy data.txt to the new directory.


```
cp data.txt /tmp/manan
```


Navigate to the new directory and check filetype of data.txt.


```
cd /tmp/manan
```



```
file data.txt
```


Use xxd command to reverse the hex dump.


```
xxd -r data.txt data1
```


Check file type of data1


```
file data1
```


Since it is a gzip compressed data, we’ll decompress it to data2 after changing its type to gzip.


```
mv data1 data2.gz
```



```
gzip -d data2.gz
```


Check filetype of data2.


```
file data2
```


Since, it is a bzip2 compressed file, we’ll decompress it to data3 after changing its type to bzip2.


```
mv data2 data3.bz2
```



```
bzip2 -d data3.bz2
```


Check filetype of data3.


```
file data3
```


Since it is a gzip compressed data, we’ll repeat the previous steps.


```
mv data3 data4.gz
```



```
gzip -d data4.gz
```


Check filetype of data4.


```
file data4
```


It is a POSIX tar archive. So, use tar command to decompress it.


```
tar -xf data4
```


Check to see that a new file “data5.bin” is extracted. Check its filetype.


```
file data5.bin
```


It is a POSIX tar archive. So, repeat the previous process. A new file “data6.bin” is extracted. Check its filetype.


```
tar -xf data5.bin
```



```
file data6.bin
```


Since it is a bzip2 compressed file, repeat the previous process.


```
mv data6.bin data7.bz2
```



```
bzip2 -d data7.bz2
```


Check filetype of data7.


```
file data7
```


It is a POSIX tar archive. So, repeat the previous process. A new file “data8.bin” is extracted. Check its filetype.


```
tar -xf data7
```



```
file data8.bin
```


Since it is a gzip compressed data, we’ll repeat the previous steps.


```
mv data8.bin data9.gz
```



```
gzip -d data9.gz
```


Check filetype of data9.


```
file data9
```


It is ASCII text. So view its content using cat command.


```
cat data9
```


Password - FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## **Level 13 → Level 14**

Use ls command to see that there is a private key “sshkey.private” which can only be read by the user bandit14 which we will have to connect using localhost and the private key.


```
ssh bandit14@localhost -i sshkey.private -p 2220
```


Use cat command on the given path to get the password.


```
cat /etc/bandit_pass/bandit14
```


Password - MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

## **Level 14 → Level 15**

Use telnet or nc command to connect to localhost on port 30000 and paste the password of this level to get the next password.


```
telnet localhost 30000
```
 or 


```
nc localhost 30000
```


Password - 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo