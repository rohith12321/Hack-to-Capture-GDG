Since this is a .rar file, any of the normal steganographic methods wouldn't work. So i used binwalk to try and see what the file contains.
```bash
binwalk --dd=".*" Santa.rar
```

Observed that this extraction gave rise to 3 directories, now opened each of them and checked for the files. I saw 2 images in one of the directories.

Ran exiftool and binwalk on these images to extract whatever extra present.
```bash
cd _Santa.rar.extracted
ls
exiftool 1.png
exiftool 3.png
binwalk --dd=".*" 1.png
binwalk --dd=".*" 3.png
ls
```
Now there are more directories which are the binwalk extracted portions from the image. Checking these directories for clues.

```bash
cd _3.png.extracted
ls
file *
exiftool 0
exiftool CCB6
```
The first image has trailer data while the second image is safe.

```bash
binwalk --dd=".*" 0
ls
cd _0.extracted
file *
exifitool 0
exiftool CCB6
binwalk --dd=".*" 0
ls
cd _0.extracted
```
Here we observe that binwalk extraction is just giving the same file again and again, so maybe 3.png does not contain any secret data of our use.

```bash
cd ~/Downloads/_Santa.rar.extracted
ls
cd _1.png.extracted
file *
exiftool 36
binwalk --dd=".*" 36
```
No result from binwalk, so we check the binary data using -b

```bash
exiftool -b -RedToneReproductionCurve 36 > red_curve.bin
exiftool -b -GreenToneReproductionCurve 36 > green_curve.bin
exiftool -b -BlueToneReproductionCurve 36 > blue_curve.bin
```
But checking these reveal empty documents, so maybe this also doesn't contain anything.

```bash
cd ~/Downloads/_Santa.rar.extracted/_1.png-0.extracted
ls
cd _0.extracted
```
Again same problem, so now we stop checking this Santa extraction and start checking the other one.

```bash
cd ~/Downloads/_Santa.rar-1.extracted
file *
binwalk --dd=".*" 7C66D
```

Ran binwalk on the weird looking file and there were many extractions.

```bash
cd _7C66D.extracted
file *
exiftool AC596
binwalk --dd=".*" AC596
cd _AC596.extracted
file *



