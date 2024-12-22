# Writeup

## Level 0
```$ ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0```

## Level 1
Logged  in to bandit host  
used ```cat readme``` to open the readme file  
Got the password as ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If  
command to connect - ```$ ssh bandit1@bandit.labs.overthewire.org -p 2220```

## Level 2
Used ```cat -- ./-``` to access the "-"file  
got password 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 3
Command used to open the file: ```cat "spaces in this filename"```  
found password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 4
Used ```ls -a``` to get the hidden files  
Opened the hidden file by: ```cat ...Hiding-From_You ```  
Found password 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ 

## Level 5
Got the password in -file07   
Used ```cat -- -file07``` to open  
got password 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 6
Used ```find . -type f -size 1033c ! - executable -exec ls -lh {}\;``` to find the file with given properties.   
Used ```cat maybehere07/.file2``` to open the file  
Got password HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 7
Used ```find / -user bandit7 -group bandit6 -size 33c``` to search the file in all directories  
Got the file wth path as "/var/lib/dpkg/info/bandit7.password"  
Used ```cat [file path]``` to open the file  
Got Password as morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj  
For bandit7

## Level 8
Used ```grep "millionth" data.txt``` to find the word in the txt file  
got password as: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 9
Used ```sort data.txt | uniq -u``` to get the line  
Got password as 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 10
Used ```strings data.txt | grep "==="```   to get the readable data starting with 3 =  
Got password as FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey  
Password for bandit10

## Level 11
Used ```base64 -d data.txt``` to decode the base64 encoded file  
Got password as dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## Level 12
cat the data.txt file   
Used ```echo "7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4" | tr 'A-Za-z' 'N-ZA-Mn-za-m'``` to decode the data  
Got the password as 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## Level 13
Made a temporary archive using ```mktemp -d```  
Copied path to go to the temporary file  
Used ```cp ~/data.txt .```   to copy the file to the archive  
Used ```mv data.txt hexd```    to rename the file  
Used ```xxd -r hexd comd```    to change it to actual  
```xxd comd | head``` to get the file signature as "1f8b" which is of gzip file  
```mv comd comd.gz```    to change the extension  
```gunzip -d comd.gz``` to decompress the file  
```xxd comd```   to get next file signature 425a which is a bzip file  
```mv comd comd.bz2```  
```bunzip2 comd.bz2```   to decompress  
```xxd comp```    gets file signature as 1f8b that is again a gzip file  
```mv comd comd.gz```  
```gunzip -d comd```  
```xxd comd | head```     we see data5.bin  
```mv comd comd.tar```  
```tar -xf comd.tar```     to get data5.bin  
```file data5.bin```    gives it is also a tar archive  
```tar -xf data5.bin```     gives data6.bin  
```tar -xf data6.bin```     gives data8.bin  
```tar -xf data8.bin``` gives no further  
```file data8.bin```      shows it is a gzip file and it is max compressed  
```mv data8.bin  data8.gz```  
```gunzip -d data8.gz```      gives data8  
```cat data8``` gives password  
Password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn


## Level 14
Logged in to see sshkey.private in the home directory. Exit from server  
```scp -P 2220  bandit13@bandit.labs.overthewire.org:sshkey.private .```      to get sshkey.private file in my computer. Entered the password to get the file.  
```ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220```     to login to bandit14 but got warning unprotected private key.  
used ```chmod 700 sshkey.private```    to make myself the owner.  
```ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220```      to login to bandit14

## Level 15
```cd /etc/bandit_pass```    to open the password directory  
```cat bandit14``` gives password of bandit14 as MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS  
Used   ```nc localhost 30000```   to connect to the local host  
entered MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS to get the next password  
 Next password for bandit15 is 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo




