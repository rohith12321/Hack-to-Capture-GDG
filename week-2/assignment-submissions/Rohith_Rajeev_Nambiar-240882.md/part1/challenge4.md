Checking the newly downloaded file for it's file type gave data as file meaning it is either corrupted or that it is a fake. Running exiftool gave file format error and binwalk gave nothing.

```bash
file week-2_challenge-files_challenge4_newsong.m4a
exiftool week-2_challenge-files_challenge4_newsong.m4a
binwalk -e week-2_challenge-files_challenge4_newsong.m4a
```
Running zsteg gives error, running foremost and checking reveals that 1 file was extracted which is some video format.

```bash
zsteg week-2_challenge-files_challenge4_newsong.m4a
foremost -i week-2_challenge-files_challenge4_newsong.m4a -o output
cd ouput
cat audit.txt
cd mov
ls
file 00000000.mov
```
Running exiftool on this file tells that the media is at an offset of 8160.

This file does not support zsteg, binwalk gives no results.
```bash
zsteg 00000000.mov
binwalk -e 00000000.mov

```
