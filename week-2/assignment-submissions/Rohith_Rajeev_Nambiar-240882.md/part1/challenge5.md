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
The author thing asks if there is a password in this, so I open this mp3 with sonic visualizer and make a spectogram to analyse. It has some text which should be the password. But we do not know which file this is the password for. Stored that password in a file named pass.txt
```bash
cat > pass.txt      
sp3ctrum_1s_y0ur_fr13nd
```
Now that the filetype of the .rar file is data, maybe it is corrupted. So i try to recover using rar. It converts into a rar, so i use rar2john on the recovered file to get the password hash and store it in a file. Then use the password which i got to try and unrar it.
```bash
file y0u_4r3_cl0s3.rar
rar r y0u_4r3_cl0s3.rar
file *
unrar x -p$(cat pass.txt) rebuilt.y0u_4r3_cl0s3.rar
```

I get a message saying f1n4lly.txt is extracted which was also there in the strings of the file. On opening this text doc, it looks like it is base64 text. I decode it to get some text.
```bash
cat f1n4lly.txt
cat > new.txt
ZjByM241MWNzX21hNXQzcg==
base64 -d new.txt
```
I don't think I can do anything more with this, so this should possibly be the flag.

Flag: f0r3n51cs_ma5t3r 



