Checked the filetype and ran exfitool to figure out that there's some embedded data after the image. So used binwalk and got into the file.

```bash
file megatron.png
exiftool megatron.png
binwalk --dd=".*" megatron.png
ls
cd _megatron.png.extracted
file *
exiftool 28E48
```
The message in the warning made me type in another command and then I unrar the .rar file to see if i get any more clues.
```bash
exiftool -duplicates 28E48
unrar x 28E48
file *
exiftool purrr_2.mp3
```
