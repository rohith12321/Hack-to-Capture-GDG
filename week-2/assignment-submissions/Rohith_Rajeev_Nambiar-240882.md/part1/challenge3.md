Since this is a .rar file, any of the normal steganographic methods wouldn't work. So i used binwalk to try and see what the file contains.
```bash
binwalk --dd=".*" Santa.rar
```

Observed that this extraction gave rise to 3 directories, now opened each of them and checked for the files. I saw 2 images in one of the directories.
Used zsteg to check for data in these.
```bash
zsteg 3.png
zsteg 1.png
```
'1169169 bytes of extra data after image end (IEND), offset = 0xccb6' - This was the result from the first command.

So I copied only the later files into a different file to analyze it further. The offset is the value to skip.

```bash
dd if=3.png of=extra_data.bin bs=1 skip=84022
file extra_data_bin
strings extra_data_bin
```
This is of data filetype. So checked for strings but found nothing interesting.

The second command gave some secret key and public key in some lines. So hoping that this will give some info.

```bash
zsteg -E b1,b,lsb,xy 1.png > secret_key1.asc
zsteg -E b4,b,lsb,xy 1.png > public_key.asc 
zsteg -E b3,bgr,msb,xy 1.png > secret_key2.asc
file secret_key1.asc
file secret_key2.asc
file public_key.asc
```
