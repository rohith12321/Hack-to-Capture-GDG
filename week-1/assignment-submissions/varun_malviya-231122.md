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

## Level 4
- bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ file inhere
inhere: directory
bandit3@bandit:~$ cat inhere
cat: inhere: Is a directory
bandit3@bandit:~$ find inhere
inhere
inhere/...Hiding-From-You
bandit3@bandit:~$ find /-name "inhere"
find: ‘/-name’: No such file or directory
inhere
inhere/...Hiding-From-You
- bandit3@bandit:~$ find . -type d -name "inhere"
./inhere
bandit3@bandit:~$ ls ./inhere
bandit3@bandit:~$ cd ./inhere
bandit3@bandit:~/inhere$ ls./inhere
-bash: ls./inhere: No such file or directory
bandit3@bandit:~/inhere$ ls ./inhere
ls: cannot access './inhere': No such file or directory
bandit3@bandit:~/inhere$ cat inhere
cat: inhere: No such file or directory
bandit3@bandit:~/inhere$ ls -a ./inhere
ls: cannot access './inhere': No such file or directory
bandit3@bandit:~/inhere$ find inhere
find: ‘inhere’: No such file or directory
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -1
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat /.Hiding-From-You
cat: /.Hiding-From-You: No such file or directory
bandit3@bandit:~/inhere$  cat ./inhere/.Hiding-From-You
cat: ./inhere/.Hiding-From-You: No such file or directory
bandit3@bandit:~/inhere$  cat ./inhere/...Hiding-From-You
cat: ./inhere/...Hiding-From-You: No such file or directory
bandit3@bandit:~/inhere$ cat /...Hiding-From-You
cat: /...Hiding-From-You: No such file or directory
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ





## Level 5
- bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd ./inhere
bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
bandit4@bandit:~/inhere$ ls -1
-file00
-file01
-file02
-file03
-file04
-file05
-file06
-file07
-file08
-file09
bandit4@bandit:~/inhere$ find . -type f -exec file {} \;
./-file08: data
./-file02: data
./-file09: data
./-file01: data
./-file00: data
./-file05: data
./-file07: ASCII text
./-file03: data
./-file06: data
./-file04: data
bandit4@bandit:~/inhere$ cat -file07
cat: invalid option -- 'f'
Try 'cat --help' for more information.
bandit4@bandit:~/inhere$ cat file07
cat: file07: No such file or directory
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
bandit4@bandit:~/inhere$ cat <./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw



## Level 6
- bandit5@bandit:~/inhere$ ls -l
total 80
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere00
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere01
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere02
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere03
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere04
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere05
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere06
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere07
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere08
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere09
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere10
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere11
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere12
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere13
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere14
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere15
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere16
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere17
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere18
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere19
bandit5@bandit:~/inhere$ file */{.,}* | grep "ASCII text" | grep -v ', with very long lines'
maybehere10/.file2:       ASCII text
maybehere15/.file2:       ASCII text
maybehere01/-file2:       ASCII text
maybehere08/spaces file1: ASCII text
maybehere12/-file2:       ASCII text
maybehere15/spaces file2: ASCII text
maybehere18/-file2:       ASCII text
bandit5@bandit:~/inhere$ find . -type f -size 1033c ! -executable -exec file '{}' \; | grep ASCII
./maybehere07/.file2: ASCII text, with very long lines (1000)
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
## Level 7
- 
## Level 8
## Level 9
## Level 10
## Level 11
## Level 12
## Level 13
## Level 14
## Level 15






