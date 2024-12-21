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
- I used the ls command to list the files in the directory and found a file named spaces in this filename, which contains spaces in its name.
- To confirm its type, I attempted to use the file command but initially faced errors due to the spaces in the file name.
- I realized that spaces needed to be escaped using backslashes (\) to properly reference the file name.
- I used the command cat spaces\ in\ this\ filename to read the file's content successfully.
- This revealed the file's content: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx.

## Level 4
- I used the ls command and found a directory named inhere.
- To confirm, I checked its type using the file inhere command and verified it was a directory.
- I tried to use cat inhere directly but received an error because it is a directory.
- I used the find command and discovered a hidden file named ...Hiding-From-You inside the inhere directory.
- Navigating into the inhere directory, I used the ls -a command to list all files, including hidden ones, and located ...Hiding-From-You.
- Finally, I used the cat ...Hiding-From-You command to read the content of the hidden file.
- This revealed the file’s content: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ.




## Level 5
- I listed the files in the inhere directory using the ls command and found multiple files named -file00, -file01, etc.
- To view them in a single-column format, I used the ls -1 command.
- I identified the file types using the find . -type f -exec file {} \; command. This revealed that -file07 is an ASCII text file.
- When I tried to use cat -file07, it failed because the file name starts with a dash (-), which is interpreted as an option by the cat command.
- To resolve this, I used cat ./-file07, explicitly specifying the path to the file to avoid treating it as an option.
- I also used input redirection with cat < ./-file07 as an alternative method.
- Both commands successfully displayed the file content: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw.



## Level 6
- I used the ls -l command to list all the directories inside the inhere folder and observed that it contained multiple subdirectories named maybehere00, maybehere01, etc.
- To identify files containing ASCII text, I used the command file */{.,}* | grep "ASCII text". This searched for ASCII text files across all directories, including hidden files, and excluded those with "very long lines."
- This revealed files such as maybehere10/.file2 and maybehere15/spaces file2.
- I needed to find the specific file based on its size and non-executable status. I ran the command: find . -type f -size 1033c ! -executable -exec file '{}' \; | grep ASCII
- This located ./maybehere07/.file2, which matched the criteria.
- Finally, I used the cat ./maybehere07/.file2 command to display the content of the file.
- The file content was: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG.




## Level 7
- I used the find command to locate a file that matches specific criteria. The task was to identify a file:
Owned by the user bandit7.
Belonging to the group bandit6.
With a size of exactly 33 bytes.
- The command I executed was:
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null  
- find /: Searches from the root directory.
- -type f: Specifies that the search is for files.
- -user bandit7: Filters files owned by the bandit7 user.
- -group bandit6: Filters files belonging to the bandit6 group.
- -size 33c: Specifies files with a size of 33 bytes.
- 2>/dev/null: Redirects error messages (e.g., permission denied) to /dev/null for cleaner output.
- The command output revealed the file path:
/var/lib/dpkg/info/bandit7.password  
- To read the content of this file, I used the cat command:
cat /var/lib/dpkg/info/bandit7.password  
- The file contained the password:
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj  
## Level 8
- I used the grep command with a regular expression to extract the text following the word "millionth" in the data.txt file.

- The regular expression (?<=millionth).+ searches for any text that appears after the word "millionth".

- The extracted text from the file was:
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

- This was the result I needed for the task.
## Level 9
- I listed the files in the current directory and found that data.txt was present.

- I then used the sort command to sort the contents of data.txt and uniq -u to filter and display only the unique lines that appear once in the file.

- The unique line that appeared once in the file was:
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

- This was the result I needed for the task.
## Level 10
-  I used the strings command on data.txt to extract printable strings from the file.

- I then used grep to filter for lines that contain the pattern ====, and the output revealed the following strings:

3JprD,
passwordi,
is,
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
- The final string FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey was identified as the password.
## Level 11
- I listed the files in the current directory and found that data.txt was present.

- I checked the file's details using ls -l and saw that it had a size of 69 bytes and was owned by bandit11 with read permissions for bandit10.

- I viewed the content of data.txt using cat, and the file contained a base64 encoded string: VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==

- I used the base64 -d command to decode the base64 string, and the result was: The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

- The decoded string revealed the password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr.
## Level 12
-  I listed the files in the current directory and found that data.txt was present.

- I checked the file's details using ls -l and saw that it had a size of 49 bytes and was owned by bandit12 with read permissions for bandit11.

- I viewed the content of data.txt using cat, and the file contained a string: Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4

- I used the tr command to apply the ROT13 transformation (a letter substitution cipher that shifts each letter by 13 places). The command: cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

- The transformed result was: The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

- The decoded password is: 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4.
## Level 13
- Initial Setup and File Inspection:

- Command: ls
Explanation: This command lists the files in the current directory. Initially, it shows the data.txt file in the home directory (~).
- Checking the File Type:

Command: file data.txt
- Explanation: The file command is used to determine the file type. It shows that the data.txt file is an ASCII text file.
Creating a Temporary Directory:

- Command: cd /tmp

Explanation: This command changes the current working directory to /tmp, which is typically used for temporary files.

- Command: mktemp -d

Explanation: mktemp -d creates a new temporary directory. The output here is /tmp/tmp.98FWLhyKtz.

- Copying the Data File:

Command: used cp  .
Explanation: This command copies the data.txt file from the home directory (~) to the temporary directory 
- Renaming the File:

Command: mv data.txt hexdump_data
Explanation: The mv command renames the file from data.txt to hexdump_data.
- Previewing the File Content:

Command: cat hexdump_data | head
Explanation: This command displays the first few lines (default of 10) of the hexdump_data file. It shows the raw hexadecimal content.
- Reversing the Hex Dump:

Command: xxd -r hexdump_data compressed_data
Explanation: The xxd -r command reverses the hexadecimal dump in the hexdump_data file and creates a binary file named compressed_data.
- Renaming the Binary File for Compression:

Command: mv compressed_data compressed_data.gz
Explanation: The binary file compressed_data is renamed to compressed_data.gz to indicate it is a compressed file.
- Decompressing the File Using Gzip:

Command: gzip -d compressed_data.gz
Explanation: The gzip -d command decompresses the compressed_data.gz file and restores the original compressed_data file.
- Re-Renaming the Binary File:

Command: mv compressed_data compressed_data.bz2
Explanation: The file compressed_data is renamed again to compressed_data.bz2 to indicate it should be in a Bzip2 compressed format.
- Decompressing the Bzip2 File:

Command: bzip2 -d compressed_data.bz2
Explanation: The bzip2 -d command decompresses the compressed_data.bz2 file, returning it to its original form, compressed_data.
- Further Renaming the File:

Command: mv compressed_data compressed_data.tar
Explanation: The file is renamed again, this time to compressed_data.tar, indicating that it is a tar archive.
- Extracting the Tar Archive:

Command: tar -xf compressed_data.tar
Explanation: The tar -xf command extracts the contents of the compressed_data.tar archive, which now contains other files (e.g., data5.bin).
- Listing the Extracted Files:

Command: ls
Explanation: This lists the files in the current directory, showing compressed_data.tar and data5.bin.
Extracting a New Tar File:

- Command: tar -xf data5.bin
Explanation: The tar -xf command is used again to extract the contents of the data5.bin file, which may contain additional files or data.
Hex Dump of the Final File:

- Command: xxd data6.bin
Explanation: Finally, the xxd command is used to display the hex dump of data6.bin, showing the binary content in hexadecimal format.

## Level 14
- Run the following command to download the private key file from bandit13:
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
- Log in to the next level, bandit14, using the downloaded private key file:
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220

## Level 15
- Once logged in, retrieve the password for bandit14 by reading the file /etc/bandit_pass/bandit14:
- cat /etc/bandit_pass/bandit14
- The output will be:
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
- Next, use nc (Netcat) to connect to the service running on localhost at port 30000:

nc localhost 30000
- You was prompted for the password, therefore Entered the password that i have obtained earlier:
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
- Upon entering the correct password, i receive a new password for the next level:
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo






