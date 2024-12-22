# Over the Wire 

## Level 0-1
- Need to open the file readme
```bash
cat readme
```
- Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1-2
- to read a file named '-'
```bash
cat ./-
```
- Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2-3
- to read a file with spaces in it's name, use "\ "
```bash
cat spaces\ in\ this\ filename
```
- Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Level 3-4
- Go to the directory inhere
```bash
cd inhere
```
- Now, we need to see all the files here, even the hidden ones
```bash 
ls -a
```
- Now, just read the required file
```bash
cat ...Hiding-From-You
```
- Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4-5

- We can obtain the type of file in the entire doc by simply using the following command
```bash
file inhere/*
```
- This would give the output as the file types of all the files. Then we can simply read the file which is human readable(ASCII)
```bash
cat inhere/-file07
```
- Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5-6
- Now, this is a bit tricky. Since just human readable does not really reduces our search, we can first see which files are of size 1033 bytes and are non executable
```bash
find -type f -size 1033c ! -executable
```
- This gives all the files with a file size of 1033 bytes, and are non executable. Since there is only one file, that contains our password.

- Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 6-7
- We need to use the find command such that we get the files owned by bandit7 user, bandit6 group and has size of 33 bytes
```bash
find / -type f -user bandit7 -group bandit6 -size 33c
```
- This would also print all the error messages which we get due to not having permission of certain folders. To not print them, we use this command.
```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
- Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Level 7-8
- Simply read the file and use the grep command to search for the word millionth
```bash
cat data.txt | grep "millionth"
```
- Password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 8-9
- We need to sort the file data.txt and then using the uniq command to get the unique lines present. We need to sort this because uniq -u only considers duplicate lines which are adjacent.
```bash
sort data.txt | uniq -u
```
- Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 9-10
- To solve this, we would use the strings command, which would give us a list of all the printable sequences, followed by a grep statement
```bash
strings data.txt | grep "="
```
- This would give us all the printable strings which contain the symbol = in them, we can also replace this by multiple = signs, as it is given in the statement that there are many of them before the actual password
- Out of the few lines given out as the output, we can easily see the password.
- Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Level 10-11
- Simply use the base64 decode command statement
```bash
base64 --decode data.txt
```
- Password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## Level 11-12
- We are going to use the tr command to remap all the alphabets.
```bash
cat data.txt | tr 'N-ZA-Mn-za-m' 'A-Za-z'
```
- This rotates all the alphabets back by 13 positions, which would give us the original string.

- Password: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## Level 12-13
- Make a directory in /tmp 
```bash
mktemp -d
```
This would return the name of the directory made

- Then copy the file data.txt to our directory, and rename it.
```bash
cp ~/data.txt .
mv data.txt compress
```

- Now, as it is a hexdump, then we can decompress it using xxd
```bash
xxd -r compress > newcompress
```
This would give us a decompressed version of the file compress, however, as the original file was repeatedly compress, we would have to repeatedly decompress it.
We can find the type of compression using the file command
```bash
file newcompress
```
This says that it is a gzip compressed file.

- To decompress gzip file, we need to rename given file so that gzip can decompress it
```bash
mv newcompress newcompress.gz
gzip -d newcompress.gz
```
Now all we have to do is keep repeating these steps.
```bash
file newcompress
```

This tells us that now this is bzip2 compressed, hence, to decompress this,
```bash
mv newcompress newcompress.bz2
bzip2 -d newcompress.bz2
file newcompress
```
Now we get that it is again a gzip compressed file, so we need to decompress it again, just like before.
```bash
mv newcompress newcompress.gz
gzip -d newcompress.gz
file newcompress
```
Now, we see that it is a tar archive, and we need to extract from it.
```bash
mv newcompress newcompress.tar
tar -x -f newcompress.tar
```
This gives us a file named 'data5.bin'. To get it's file type, we again use the file command.
```bash
file data5.bin
```
Now we need to extract again from data5.bin,
```bash
tar -x -f data5.bin
```
This gives us another file named data6.bin, which is again a bzip2 compressed file. To recompress it, follow the above steps again
```bash
mv data6.bin data6.bz2
bzip2 -d data6.bz2
```
This gives us another tar archive, which we would extract like just like before.
```bash
mv data6 data6.tar
tar -x -f data6.tar
```
Finally we obtain a file 'data8.bin', which is a gzip compressed file, which we again decompress like we did above.
```bash 
mv data8.bin data8.gz
gzip -d data8.gz
```
This finally gives us the file data8, which contains the password...

- Password: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## Level 13-14
- All we need to do is to read the private key.
```bash
cat sshkey.private
```
- Now to get to the next level, we need to copy this key to a file.
```bash
nano privatekey
```
Paste the key in the file and save it.(Yeah I use nano ;-;)

## Level 14-15
- To log in the level 14, use ssh and the private key for it. But first we need to prepare the security key.
```bash
chmod 600 privatekey
```ssh -i {path_to_the_private_key} bandit14@bandit.labs.overthewire.org -p 2220
```
- Now simply read the file, whose location is given in the previous level.
```bash
cat  /etc/bandit_pass/bandit14
```
- We obtain the password to be MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS.
However this is not the end. We need to submit this password to port 30000 on local host.
```bash
nc localhost
```
Now just paster the password read in the previous step. Now you will obtain a new password.
- Password: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo