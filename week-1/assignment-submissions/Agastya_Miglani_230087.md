# Level 0

To solve this level and get the password I used ls and cat command.

    -- > ls
  
    -- > cat readme

# Level 1

I searched for how to read files starting with '-' and used th information to solve the first level

    -- > cat < -

# Level 2

For this level I just enclose the entire name including space in apostrophe(') to pass it as a single argument

    -- > cat 'spaces in this filename'

# Level 3

For this level I first change my directory to inhere

    -- > cd inhere

Then I list all the directories using (-a) which I found by looking at the manual for ls command

    -- > ls -a
    
Then I simply open the hidden files using cat command

    -- > cat .hidden

# Level 4

My first thought was to open individual file but that would not have worked if the number of files was really large
So I searched for way to find file types and finally used the following command to find out my desired file

    -- > file ./-file*

# Level 5

For this level I used the find command to narrow down my search by using the following attributes

    -- > find . -size 1033c ! -executable

# Level 6

First I tried the following command to filter out the file by specifying the user

    -- > find -size 33c -user bandit7 -group bandit6

But this led me nowhere so I found out how to conduct the search in the subdirectories also and used a slash(/) before the attributes.
After that I got a lot of error messages and only one file amongst the list had no error message so I opened that file to get the password.

Note :- I could also have used 2>/dev/null to remove all the files with error messages from the list

# Level 7

For this level I just used grep with cat to filter out the line with the word millionth

    -- > cat data.txt | grep "millionth"

# Level 8

I used sort command and piped its ouput to uniq command to get the passowrd

    -- > sort data.txt | uniq -c

Note :- I could also have used

    -- > sort data.txt | uniq -c| sort -k 1n| head -1

# Level 9

For this level I used strings function to print parts with readable string format and piped the ouput to
grep function which I used to print lines with multipl '=' symbols

    -- > strings data.txt | grep "===="

# Level 10

For this level I read about base64 function and used the -d attribute to decode the given text

    -- > base -64 -d data.txt

# Level 11

For this level I simply used tr function along with cat to rotate the characters by 13 alphabets

    -- > cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

# Level 12

first I moved the file to a new director where I reversed the hexdump to binary which then I read using

    -- > xxd ans | head

After then I searched for th files signatures of then I converted the file to new file type by

    -- > mv ans ans.*filetype*

After repeating this process a few times over I got the password

# Level 13

First I copied the sshkey from web to my computer by using the following command

    -- > scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private ./new

Then I give all the required permission to myself using

    -- > chmod 700 sshkey.private

Then I login to level 14 using
    
    -- > ssh -i *key_location* bandit14@bandit.labs.overthewire.org -p 2220

# Level 14

I used the netcat command to shift to a different port then I inpu the previous password for my new password

    -- > nc localhost 30000

# Level 15

Since nc cann't connect to a port using ssl encryption I would have to use ssl command

    -- > openssl s_client -connect localhost:30001
