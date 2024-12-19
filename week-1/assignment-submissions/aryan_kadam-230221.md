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
