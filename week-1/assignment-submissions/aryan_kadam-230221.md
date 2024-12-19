# WRITEUP #
# LEVEL 0 #
Use ssh to connect to the host with the given username and port number and then login using the password. This will be used to login for each level just the username will get changed according to the level for eg bandit2 instead of bandit0 , etc.
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
# LEVEL 1 #
Given that the password is in file called readme in the home directory , first we list all the files present and then open the readme file using cat command. Then we login to the next level using the psasword we got.
```
ls
cat readme
```
#### PASSWORD -> ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If ####
# LEVEL 2 #
First we list the files present using ls. Then we see a file named "-" but if we do cat - it won't work as cat - will wait for stdin (e.g.,keyboard input). Thus we can use either of the following commands.
```
cat < - OR cat ./-
```
#### PASSWORD -> 263JGJPfgU6LtdEvgfWU1XP5yac29mFx ####
# LEVEL 3 #
We list all the files and find a file named "spaces in this filename" . To open such files we need to write the cat command in the following manner.
```
cat "spaces in this filename"
```
#### PASSWORD -> MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx ####
# LEVEL 4 #
Given the file is located in "inhere" directory , we first list all the files and directories using ls and we find a inhere directory. We navigate to it using cd command and use the following option of the ls command to view all the files including the hidden ones (ls -a where -a stands for all), and we find a file named "...Hiding-From-You".
```
ls
cd inhere
ls -a
cat "...Hiding-From-You"
```
#### PASSWORD -> 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ ####
# LEVEL 5 #
First we navigate to the inhere directory similarly how we did before. We now list the files present in the inhere directory where we find 10 files. I manually opened all the files using cat and found the password in -file07.
Also if we check the type of the file for every file other than -file07 the type is data , whereas -file07 's type is ASCII text.
```
ls
cd inhere
cat ./-file00 till cat./-file07
file ./-file07
```
#### PASSWORD -> 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw ####
# LEVEL 6 #
Given the file is in inhere directory with the following properties -
human-readable
1033 bytes in size
not executable
Once we navigate to the directory and use ls we see many directories named maybehere. So inorder to find the file's location I used the following command by which i got that the file's path is ./maybehere07/.file2.
```
ls
cd inhere
ls
find -size 1033c -readable ! -executable
cat ./maybehere07/.file2
```
We used the -size option and specified that 1033 bytes (c represents bytes) is the size of the file we are looking for along with the -readable and ! -executable option where ! stands for 'not'.
#### PASSWORD -> HWasnPhtq9AVKe0dmk45nxy20cvUa6EG ####
# LEVEL 7 #
Given that we want to find the password which is stored somehwere on the server with the following properties 
owned by user bandit7
owned by group bandit6
33 bytes in size
On doing ls we don't get anything significant thus we perfom a search for the file starting from the root with the above properties using the following command
```
find / -type f -size 33c -user bandit7 -group bandit6
```
On doing this we get a list of paths to different files among which one is /var/lib/dpkg/info/bandit7.password. Inorder to navigate to var we need to be in the root so we execute the following commands
```
cd /
cat /var/lib/dpkg/info/bandit7.password
```
#### PASSWORD -> morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj ####
# LEVEL 8 #
This is a simple task involving the use of the grep command.
```
grep "millionth" data.txt
```
#### PASSWORD -> dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc ####
# LEVEL 9 #
Inorder to solve this question we need to understand how the command works. When we only use uniq it compares only the consecutive lines therefore uniq -u  (-u only prints unique lines => man uniq ) . uniq -u command will return only the lines that occur exactly once among the consecutive lines in its input. So inorder to bring all the occurences together I sorted the file and then used uniq command as follows
```
sort data.txt | uniq -u
```
#### PASSWORD -> 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM ####
# LEVEL 10 #
Given that the password is stored in data.txt after a set of 'equal to' signs in one of the human-readable strings , we can use the strings command . On opening the man page for strings we find 
"strings - print the sequences of printable characters in files " which is why this command can be used to find the password. On using this we find 4 strings which have several equal to signs but only one looks like a password i.e D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey.
```
strings data.txt
```
#### PASSWORD -> FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey ####
# LEVEL 11 #
Using the man page of base64 we see that inorder to decode a file we use the -d option , so its simple enough
```
base64 -d data.txt
```
The text translates to the password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr.
#### PASSWORD -> dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr ####
# LEVEL 12 #
This is ROT13 cipher , so we can use translate command (tr) . When A is shifted 13 times it becomes a N. This is the transformation which we give to the command as follows
```
tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
```
#### PASSWORD -> 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4 ####
# LEVEL 13 #
Initially I looked at all the man pages for the commands mentioned , then due to limited permissions we were told to work in a separate directory , so i made a directory inside tmp and copied the data.txt file there. As it was a hexdump of a file which was repeatedly compressed i used xxd command and stored it to another file called data. Then i checked the type of file data is , and it was gzip compressed data which had data2.bin.

So inorder to decompress we first need to add the suffix .gz to data and then move ahead . On decompressing we get another file called data which is bzip2 compressed. So do decompress that i used the bzip command which leads us to a data.out file which is in turn gzip compressed. Again adding the suffix and decompressing it we get a file named data which is a POSIX tar archive. Using tar command we extract the data and get data5.bin which is again a tar archived file. Extracting the files again i get a bzip2 compressed file named data6.bin.

Decompressing the above file i get data6.bin.out which is a tar archived file. Extracting it i get a data8.bin which is a gzip compressed file which we decompress as we did above and finally get a file data8 which contains the password.

Here are the commands which i used
```
mkdir /tmp/aryan
cp data.txt /tmp/aryan
cd ..
cd ..
cd /tmp/aryan
xxd -r data.txt > data
file data
mv data data.gz
gzip -d data.gz
file data
bzip2 -d data
file data.out
mv data.out data.gz
gzip -d data.gz
file data
tar -xf data
file data5.bin
tar -xf data5.bin
file data6.bin
bzip2 -d data6.bin
file data6.out
tar -xf data6.out
file data8.bin
mv data8.bin data8.gz
gzip -d data8.gz
cat data8
```
#### PASSWORD -> FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn ####
# LEVEL 14 #
Looking at the man page of ssh i found the -i option which tells SSH to use the specified file as the private key for the authentication process. Thus I used sshkey.private and connected to the server using the following
```
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```
# LEVEL 15 #
We get the password according the instructions given in the previous level
```
cd ..
cd ..
cat /etc/bandit_pass/bandit14
```
#### PASSWORD TO BE USED -> MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS ####
I searched how to connect to localhost on a particular port , and I found that netcat allows us to do it as follows
```
nc localhost 30000
```
On entering the password above I get the following password
#### PASSWORD -> 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo ####
 


