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
- bandit6@bandit:~$ find / -type f -user bandit7 -group bandit6 -size 33c 2>/d
ev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
## Level 8
- bandit7@bandit:~$ grep -oP '(?<=millionth).+' data.txt
        dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
## Level 9
- bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
## Level 10
-  strings data.txt | grep ====
}========== the
3JprD========== passwordi
~fDV3========== is
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
## Level 11
- bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit11 bandit10 69 Sep 19 07:08 data.txt
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
bandit10@bandit:~$ base64 -d data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
## Level 12
-  ls -l
total 4
-rw-r----- 1 bandit12 bandit11 49 Sep 19 07:08 data.txt
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
## Level 13
- bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ file data.txt
data.txt: ASCII text
bandit12@bandit:~$ cd /tmp
bandit12@bandit:/tmp$ mktemp -d
/tmp/tmp.98FWLhyKtz
bandit12@bandit:/tmp$ cd /tmp/tmp.98FWLhyKtz
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ cp ~/data.txt .
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
data.txt
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ mv data.txt hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ cat hexdump_data | head
00000000: 1f8b 0808 dfcd eb66 0203 6461 7461 322e  .......f..data2.
00000010: 6269 6e00 013e 02c1 fd42 5a68 3931 4159  bin..>...BZh91AY
00000020: 2653 59ca 83b2 c100 0017 7fff dff3 f4a7  &SY.............
00000030: fc9f fefe f2f3 cffe f5ff ffdd bf7e 5bfe  .............~[.
00000040: faff dfbe 97aa 6fff f0de edf7 b001 3b56  ......o.......;V
00000050: 0400 0034 d000 0000 0069 a1a1 a000 0343  ...4.....i.....C
00000060: 4686 4341 a680 068d 1a69 a0d0 0068 d1a0  F.CA.....i...h..
00000070: 1906 1193 0433 5193 d4c6 5103 4646 9a34  .....3Q...Q.FF.4
00000080: 0000 d320 0680 0003 264d 0346 8683 d21a  ... ....&M.F....
00000090: 0686 8064 3400 0189 a683 4fd5 0190 001e  ...d4.....O.....
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ xxd -r hexdump_data compressed_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
compressed_data  hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ mv compressed_data compressed_data.gz
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
compressed_data.gz  hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ gzip -d compressed_data.gz
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
compressed_data  hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ xxd compressed_data
00000000: 425a 6839 3141 5926 5359 ca83 b2c1 0000  BZh91AY&SY......
00000010: 177f ffdf f3f4 a7fc 9ffe fef2 f3cf fef5  ................
00000020: ffff ddbf 7e5b fefa ffdf be97 aa6f fff0  ....~[.......o..
00000030: deed f7b0 013b 5604 0000 34d0 0000 0000  .....;V...4.....
00000040: 69a1 a1a0 0003 4346 8643 41a6 8006 8d1a  i.....CF.CA.....
00000050: 69a0 d000 68d1 a019 0611 9304 3351 93d4  i...h.......3Q..
00000060: c651 0346 469a 3400 00d3 2006 8000 0326  .Q.FF.4... ....&
00000070: 4d03 4686 83d2 1a06 8680 6434 0001 89a6  M.F.......d4....
00000080: 834f d501 9000 1e90 34d1 8803 430e 9a0c  .O......4...C...
00000090: 4069 a006 2646 8683 4003 10d3 4034 69a6  @i..&F..@...@4i.
000000a0: 8068 0000 068d 0d00 6806 080d 1a64 d346  .h......h....d.F
000000b0: 9a1a 68c9 a680 309a 6868 0181 0132 0401  ..h...0.hh...2..
000000c0: 2aca 6051 e81c ac53 2f0b 84d4 d05d b84e  *.`Q...S/....].N
000000d0: 88e1 2729 214c 8eb8 e608 4ce5 db08 35ff  ..')!L....L...5.
000000e0: 854f fc11 5a0d 0cc3 3d67 1401 2157 625e  .O..Z...=g..!Wb^
000000f0: 0cdb f1ae f9b6 a723 a61d 7b0e 0642 1401  .......#..{..B..
00000100: ddd5 39af 76f0 b4a2 2f74 4ab6 1fa3 933c  ..9.v.../tJ....<
00000110: 064e 9837 6fdc 2345 b15f 230d 8f64 0b35  .N.7o.#E._#..d.5
00000120: 34de 2941 95a7 c6de 0c74 4fd4 084a 51da  4.)A.....tO..JQ.
00000130: d3e2 0818 9b08 239f cc9c 81e5 8c94 619d  ......#.......a.
00000140: aece 4a42 8417 0661 a37f 7d13 3683 22cd  ..JB...a..}.6.".
00000150: 59e2 b59f 518d 99c3 002a 9ddd 3068 f4f9  Y...Q....*..0h..
00000160: f67d b693 eaed 9add 7c89 1a12 2109 2697  .}......|...!.&.
00000170: ea6e 0595 2291 f17b d30b a447 196f 370c  .n.."..{...G.o7.
00000180: 360f 6102 aede a9b5 2ffc 4697 9238 98b9  6.a...../.F..8..
00000190: 5336 c4c2 47ce b18a 5337 9f48 3152 a341  S6..G...S7.H1R.A
000001a0: e9fa 269d 6c28 f424 eae3 9465 1dcb 5ca9  ..&.l(.$...e..\.
000001b0: 6cd5 05d9 86da 2247 f4d5 8b58 9d56 7a92  l....."G...X.Vz.
000001c0: 0b85 8ea9 5c63 c125 0961 2c53 648e 7d24  ....\c.%.a,Sd.}$
000001d0: 0280 8e9b 6002 b413 c7be 0a1a e314 0047  ....`..........G
000001e0: 9643 70ef c09b 43a4 cb88 2a4a ae4b 81ab  .Cp...C...*J.K..
000001f0: f71c 1467 f78a 3408 67e5 b61d f6b0 e880  ...g..4.g.......
00000200: 236d 1c41 6a28 d0c4 6016 04bb a32e 5229  #m.Aj(..`.....R)
00000210: 7d87 884e 30e1 f926 468f 5d30 6226 28c9  }..N0..&F.]0b&(.
00000220: 4e90 4b67 5438 9142 1f4a 9f9f eb2e c983  N.KgT8.B.J......
00000230: e2c2 0ffc 5dc9 14e1 4243 2a0e cb04       ....]...BC*...
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ mv compressed_data compressed_data.bz2
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
compressed_data.bz2  hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ bzip2 -d compressed_data.bz2
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ mv compressed_data compressed_data.gz
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ gzip -d compressed_data.gz
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ mv compressed_data compressed_data.tar
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ tar -xf compressed_data.tar
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
compressed_data.tar  data5.bin  hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ tar -xf data5.bin
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ xxd data6.bin
00000000: 425a 6839 3141 5926 5359 d0e6 93b3 0000  BZh91AY&SY......
00000010: 8c7f cfdc 6a00 40c0 7dff e120 5b23 8075  ....j.@.}.. [#.u
00000020: 21fe 8000 0840 0000 6682 0188 084c 0820  !....@..f....L.
00000030: 0094 0d53 53d3 4468 621a 0d06 8d1a 0d32  ...SS.Dhb......2
00000040: 1a64 c9a3 46d4 c8f5 0692 1a46 2626 81a3  .d..F......F&&..
00000050: 4c4c 8d34 6800 680c 2343 73dd 790f e408  LL.4h.h.#Cs.y...
00000060: 0c07 0081 0399 c714 0e85 154c 5c31 1101  ...........L\1..
00000070: f379 c1cd dedc 7623 350b 4c58 78cd bbc4  .y....v#5.LXx...
00000080: 346d a608 5f61 8680 4a36 4044 49ec 74c4  4m.._a..J6@DI.t.
00000090: d04a bf15 dc26 285d 5309 2351 5118 44e2  .J...&(]S.#QQ.D.
000000a0: c962 3545 956e cbca e3c4 72e0 e895 01a1  .b5E.n....r.....
000000b0: f79a 3d8a 4400 e29e eddd f35a 8131 5d47  ..=.D......Z.1]G
000000c0: 078a a7cf 272f 8865 b257 4227 420a f2a9  ....'/.e.WB'B...
000000d0: 0480 fe2e e48a 70a1 21a1 cd27 66         ......p.!..'f
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
compressed_data.tar  data5.bin  data6.bin.out  hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ tar -xf data6.bin.out
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
compressed_data.tar  data5.bin  data6.bin.out  data8.bin  hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ xxd data8.bin
00000000: 1f8b 0808 dfcd eb66 0203 6461 7461 392e  .......f..data9.
00000010: 6269 6e00 0bc9 4855 2848 2c2e 2ecf 2f4a  bin...HU(H,.../J
00000020: 51c8 2c56 70f3 374d 2977 2b4e 3648 4e4a  Q.,Vp.7M)w+N6HNJ
00000030: f4cc f430 c8b0 f032 4a0d cd2e 362a 4b09  ...0...2J...6*K.
00000040: 7129 77cc e302 003e de32 4131 0000 00    q)w....>.2A1...
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ mv data8.bin data8.gz
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ gzip -d data8.gz
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ ls
compressed_data.tar  data5.bin  data6.bin.out  data8  hexdump_data
bandit12@bandit:/tmp/tmp.98FWLhyKtz$ cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
## Level 14
-  scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
-   ssh -i sshkey.private bandit14@bandit.labs.overthewire.org
 -p 2220

## Level 15
- bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo






