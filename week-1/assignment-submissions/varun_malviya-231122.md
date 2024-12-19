## LEVEL 0 
ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0

## LEVEL 1
To retrieve the password for Level 1, I followed these steps:

Connected to the host using the SSH command:

bash
Copy code
ssh bandit0@bandit.labs.overthewire.org -p 2220
Used the pwd command to confirm the current working directory:

bash
Copy code
/home/bandit0
Searched for the password file using the find command:

Initially searched for readme.txt:
bash
Copy code
find readme.txt
Result: File not found.
Adjusted the search to locate a file named readme:
bash
Copy code
find readme
Verified the file type using the file command:

bash
Copy code
file readme
Result: Confirmed it was an ASCII text file.

Listed the directory contents to ensure the readme file was present:

Used ls to display all files.
Used ls -1 for a cleaner, one-file-per-line display.
Opened the readme file to retrieve the password using the cat command:

bash
Copy code
cat readme
Result: Displayed the password for Level 1.

The password  is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
ssh bandit1@bandit.labs.overthewire.org -p 2220

## LEVEL 2
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ pwd
/home/bandit1
bandit1@bandit:~$ file -
quit
/dev/stdin: ASCII text
bandit1@bandit:~$ cat <-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
bandit1@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

LEVEL 3


