Tried exiftool but that returned error in file format. Used file command and xxd to check first few bits but they revealed that this is not a GIF.

Used the strings command to see that there was some repeating text in it which said: 
Used ImageMagick
gamma=0.45455

```bash
  exiftool unopenable.gif
  file unopenable.gif
  xxd unopenable.gif
  strings unopenable.gif
```
