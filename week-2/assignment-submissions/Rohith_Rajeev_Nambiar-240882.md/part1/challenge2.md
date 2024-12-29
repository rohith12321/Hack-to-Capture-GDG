Tried exiftool but that returned error in file format. Used file command and xxd to check first few bits but they revealed that this is not a GIF but a corrupted GIF.

Used the strings command to see that there was some repeating text in it which said: 
Used ImageMagick
gamma=0.45455

```bash
  exiftool unopenable.gif
  file unopenable.gif
  xxd unopenable.gif
  strings unopenable.gif
```
Changed the first few bits using hexedit to 4749 4638 3961 to try and convert it to GIF as the tail part looks like GIF format.

```bash
  cp unopenable.gif new.gif
  hexedit new.gif
```
Opening the file gave me 4 different frames, which look like base64 text and there was a frame saying decode it.

```bash
  cd ~/Desktop
  touch new.txt
  cat > new.txt
  ZmxhZ3tnMWZfb3JfajFmfQ==
  base64 -d new.txt
```

Flag: flag{g1f_or_j1f}






