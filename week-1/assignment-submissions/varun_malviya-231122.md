## LEVEL 0 
ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0

## LEVEL 1
bandit0@bandit:~$ pwd
/home/bandit0
bandit0@bandit:~$ find readme.txt
find: ‘readme.txt’: No such file or directory
bandit0@bandit:~$ find readme
readme
bandit0@bandit:~$ file readme
readme: ASCII text
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ ls -1
readme
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
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


