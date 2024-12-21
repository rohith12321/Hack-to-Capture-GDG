## LEVEL 0 
- ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0

## LEVEL 1
- To retrieve the password for Level 1, I followed these steps:
- Connected to the host using the SSH command:
ssh bandit0@bandit.labs.overthewire.org -p 2220
- Used the pwd command to confirm the current working directory:
/home/bandit0
- Searched for the password file using the find command:
- Initially searched for readme.txt:
find readme.txt
Result: File not found.
- Adjusted the search to locate a file named readme:
find readme
- Verified the file type using the file command:
file readme
- Result: Confirmed it was an ASCII text file.
- Listed the directory contents to ensure the readme file was present:
- Used ls to display all files.
- Used ls -1 for a cleaner, one-file-per-line display.
- Opened the readme file to retrieve the password using the cat command:
cat readme
- Result: Displayed the password for Level 1.
- The password is:
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
- Connected to Level 1 using the SSH command:
ssh bandit1@bandit.labs.overthewire.org -p 2220

## LEVEL 2
- To retrieve the password for Level 2, I followed these steps:
Connected to the host using the SSH command.
- Confirmed the current working directory using the pwd command, which displayed /home/bandit1.
- Listed the directory contents using the ls command and found a file named -.
- Checked the file type using the file command, which revealed it was an ASCII text file.
- Used input redirection with the cat command to read the file’s content and retrieve the password:
cat <-
- The password is: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx.


## LEVEL 3
- bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ file spaces in the file name
spaces: cannot open `spaces' (No such file or directory)
in:     cannot open `in' (No such file or directory)
the:    cannot open `the' (No such file or directory)
file:   cannot open `file' (No such file or directory)
name:   cannot open `name' (No such file or directory)
bandit2@bandit:~$ file spaces\in\this\filename
spacesinthisfilename: cannot open `spacesinthisfilename' (No such file or directory)
bandit2@bandit:~$ file spaces in this filename
spaces:   cannot open `spaces' (No such file or directory)
in:       cannot open `in' (No such file or directory)
this:     cannot open `this' (No such file or directory)
filename: cannot open `filename' (No such file or directory)
bandit2@bandit:~$ file spaces\ in\ this\ filename
spaces in this filename: ASCII text
bandit2@bandit:~$ cat spaces\ in\ this\ filename
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx






