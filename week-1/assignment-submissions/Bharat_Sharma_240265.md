# Bandit Level 1 to 15

## Level 0


Using ssh command to connect to the host on port 2220 with username bandit0 and using nano editor to view readme file.
```bash
$ ssh bandit0@bandit.labs.overthewire.org -p 2220 -l bandit0
$ nano readme
```

## Level 1

Syntax to view a file starting with '-', for this we use ./

```bash
$ nano ./-
```

## Level 2

Syntax to view the file which has whitespaces in the name. 'filename'

```bash
$ nano 'spaces in this filename'
```

## Level 3
Using ls -a to view the hidden file named '...Hiding-From-You' and then reading it.

```bash
$ cd inhere
$ ls -a
$ nano ...Hiding-From-You
```

## Level 4
Using file command to view the type of data stored in the files.

```bash
$ cd inhere
$ file ./*
```
'*' here is for all the files, we can check for a particular file also.

OUTPUT:

```bash
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

We find -file07 has the password.


## Level 5
We use the 'find' command to locate our required file & read it. the syntax is:

```bash
$ find . -readable -size 1033c -not -executable
```

Here . states that we search in the current directory.

OUTPUT:

```bash
bandit5@bandit:~$ find . -readable -size 1033c -not -executable
./inhere/maybehere07/.file2
```
Then we read the file

```bash
$ nano inhere/maybehere07/.file2
```

## Level 6
Again using 'find' to locate our file

```bash
$ find / -size 33c -user bandit7 -group bandit6
```

OUTPUT:
```bash
find: ‘/drifter/drifter14_src/axTLS’: Permission denied
find: ‘/root’: Permission denied
find: ‘/snap’: Permission denied
find: ‘/tmp’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/246911/task/246911/fd/6’: No such file or directory
find: ‘/proc/246911/task/246911/fdinfo/6’: No such file or directory
find: ‘/proc/246911/fd/5’: No such file or directory
find: ‘/proc/246911/fdinfo/5’: No such file or directory
find: ‘/home/bandit31-git’: Permission denied
find: ‘/home/ubuntu’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/drifter8/chroot’: Permission denied
find: ‘/home/drifter6/data’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/lost+found’: Permission denied
find: ‘/etc/polkit-1/rules.d’: Permission denied
find: ‘/etc/multipath’: Permission denied
find: ‘/etc/stunnel’: Permission denied
find: ‘/etc/xinetd.d’: Permission denied
find: ‘/etc/credstore.encrypted’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/sudoers.d’: Permission denied
find: ‘/etc/credstore’: Permission denied
find: ‘/dev/shm’: Permission denied
find: ‘/dev/mqueue’: Permission denied
find: ‘/var/log/amazon’: Permission denied
find: ‘/var/log/unattended-upgrades’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/tmp’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/spool/bandit24’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/pollinate’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/cache/apparmor/2425d902.0’: Permission denied
find: ‘/var/cache/apparmor/baad73a1.0’: Permission denied
find: ‘/var/lib/polkit-1’: Permission denied
find: ‘/var/lib/amazon’: Permission denied
/var/lib/dpkg/info/bandit7.password
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/chrony’: Permission denied
find: ‘/var/lib/snapd/void’: Permission denied
find: ‘/var/lib/snapd/cookie’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘/var/lib/udisks2’: Permission denied
find: ‘/var/crash’: Permission denied
find: ‘/boot/efi’: Permission denied
find: ‘/boot/lost+found’: Permission denied
find: ‘/sys/kernel/tracing’: Permission denied
find: ‘/sys/kernel/debug’: Permission denied
find: ‘/sys/fs/pstore’: Permission denied
find: ‘/sys/fs/bpf’: Permission denied
find: ‘/run/lock/lvm’: Permission denied
find: ‘/run/systemd/inaccessible/dir’: Permission denied
find: ‘/run/systemd/propagate/systemd-udevd.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-resolved.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-networkd.service’: Permission denied
find: ‘/run/systemd/propagate/irqbalance.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-logind.service’: Permission denied
find: ‘/run/systemd/propagate/chrony.service’: Permission denied
find: ‘/run/systemd/propagate/polkit.service’: Permission denied
find: ‘/run/systemd/propagate/ModemManager.service’: Permission denied
find: ‘/run/systemd/propagate/fwupd.service’: Permission denied
find: ‘/run/lvm’: Permission denied
find: ‘/run/log/journal/ec2dd69f90c4a6285216f71caca9bbca’: Permission denied
find: ‘/run/cryptsetup’: Permission denied
find: ‘/run/multipath’: Permission denied
find: ‘/run/screen/S-bandit20’: Permission denied
find: ‘/run/screen/S-bandit1’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/run/user/11013’: Permission denied
find: ‘/run/user/11018’: Permission denied
find: ‘/run/user/11021’: Permission denied
find: ‘/run/user/11023’: Permission denied
find: ‘/run/user/11017’: Permission denied
find: ‘/run/user/11022’: Permission denied
find: ‘/run/user/11020’: Permission denied
find: ‘/run/user/11014’: Permission denied
find: ‘/run/user/11019’: Permission denied
find: ‘/run/user/11012’: Permission denied
find: ‘/run/user/11026’: Permission denied
find: ‘/run/user/11000’: Permission denied
find: ‘/run/user/11005’: Permission denied
find: ‘/run/user/11004’: Permission denied
find: ‘/run/user/11016’: Permission denied
find: ‘/run/user/11025’: Permission denied
find: ‘/run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘/run/user/11024’: Permission denied
find: ‘/run/user/11010’: Permission denied
find: ‘/run/user/11001’: Permission denied
find: ‘/run/user/11003’: Permission denied
find: ‘/run/user/11011’: Permission denied
find: ‘/run/user/8001’: Permission denied
find: ‘/run/user/11015’: Permission denied
find: ‘/run/user/11008’: Permission denied
find: ‘/run/user/11007’: Permission denied
find: ‘/run/user/11002’: Permission denied
find: ‘/run/user/11009’: Permission denied
find: ‘/run/user/11029’: Permission denied
find: ‘/run/chrony’: Permission denied
find: ‘/run/udisks2’: Permission denied
```
In the whole filesystem only /var/lib/dpkg/info/bandit7.password is readable hence it is our file.
## Level 7
We use nano editor to find the keyword:

```bash
$ nano data.txt
```
Press <kbd>Ctrl</kbd> + <kbd>W</kbd> and type the word 'millionth' and our password is next it

## Level 8
Here we use 'sort' & uniq -u command to find our line in the file.

```bash
$ sort data.txt | uniq -u
```
'sort' groups the repeated lines and 'uniq -u' finds the unique line.

## Level 9
We use 'strings' and 'grep' to find the line data.txt:

```bash
$ strings data.txt | grep "=="
```
Here strings lists all the human readable lines and grep find the pattern in it

OUTPUT
```bash
bandit9@bandit:~$ strings data.txt | grep "=="
}========== the
3JprD========== passwordi
~fDV3========== is
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

## Level 10
Using 'base64' command to decipher the encoded text in data.txt

```bash
$ base64 --decode data.txt
```

## Level 11
The text in data.txt is encoded by ROT13 encoding scheme. There is no direct command like base64 to decipher, so we use 'tr' command to translate it:

```bash
$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
Here 'cat data.txt' reads the content and it is passed as input to 'tr' 'A-Za-z' represents the set of characters to be replaced that is all the letters from A-Z & a-z, 'N-ZA-Mn-za-m' represents the set of characters to which the character will be replaced to that is A-M will be replaced with N-Z respectively and N-Z will be replaced with A-M respectively.


## Level 12
We first create a file in the tmp folder and copy the data.txt to it:

```bash
$ mkdir /tmp/bharat240265 || cp data.txt /tmp/bharat240265
$ cd /tmp/bharat240265
```
Then we convert the data.txt hexdump to the original file by:

```bash
$ xxd -r data.txt > original
```
We now check the file type by ```$ file original``` the output is: ```original: gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 574```
which means it is a gzip, we then decompress it by gzip but before that we change the name to original.gz:

```bash
$ mv original original.gz
$ gzip -d original.gz
```

We then obtain another file named 'original' which is of bzip2 type. Now we repeat this process again and again until we obatain an ASCII text file, we then read it to find the password. The commands used are:

```bash
$ gzip -d original.gz
$ bzip -d original.bz2
$ tar xf original.tar
```

Remember to rename the file each time after decompression accordingly to the next type




## Level 13
First we start an ssh session from the bandit13 ssh session:

```bash
$ ssh  bandit14@localhost -i sshkey.private -p 2220
```
and the read the required file to get the password

```bash
$ nano /etc/bandit_pass/bandit14
```

## Level 14
Using netcat to establish a connection to localhost:30000 & typing the previous password MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

```bash
$ nc localhost 30000
```

OUTPUT

```bash
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

## Level 15
We use openssl to do this:

```bash
$ openssl s_client -connect localhost:30001
```
