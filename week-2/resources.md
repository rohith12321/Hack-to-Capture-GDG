# Week - 2

## 1. Forensics and Steganography

**Forensics**: The art of recovering the digital trail left on a computer. There are plenty of methods to find data which is seemingly deleted, not stored, or worse, covertly recorded.

[Metadata](https://www.youtube.com/watch?v=HU_euJyxYB4&feature=youtu.be), often described as data about data, helps in understanding the history of a particular electronic file, including when the file was created, modified and accessed, among other information that can be used to describe the file.

[File signatures](https://en.wikipedia.org/wiki/List_of_file_signatures), or **magic numbers**, are unique byte sequences at the start of files that identify their format or type. They allow systems to recognize file types reliably, independent of file extensions. For example, PDFs start with 25 50 44 46 2D, and JPEGs start with FFD8. Magic numbers are essential for file verification, security, and data recovery. 

### 1) Basic Tools
- [exiftool](https://linux.die.net/man/1/exiftool)
- [file](https://linux.die.net/man/1/file) 
- [strings](https://linux.die.net/man/1/strings)
- [xxd](https://linuxhandbook.com/xxd-command/)
- [hexed.it](https://hexed.it/)
- [binwalk](https://github.com/ReFirmLabs/binwalk/wiki/Quick-Start-Guide)
- [stegsnow](https://www.kali.org/tools/stegsnow/) : White text steganography
### 2) Image forensics, steganography
- [https://www.youtube.com/watch?v=TWEXCYQKyDc](https://www.youtube.com/watch?v=TWEXCYQKyDc)
- [LSB steganography](https://medium.com/@renantkn/lsb-steganography-hiding-a-message-in-the-pixels-of-an-image-4722a8567046)


#### 2.1) Tools
- [Aperisolve](https://www.aperisolve.com/)
- [Steghide](https://github.com/StegHigh/steghide)
- [Stegseek](https://github.com/RickdeJager/stegseek) : Fast Steghide passphrase cracker
- [Zsteg](https://github.com/zed-0xff/zsteg) : Detect LSB encoding in png/bmp files
- Jpgsteg : Detect LSB encoding in JPG files
- [foremost](https://www.kali.org/tools/foremost/) : A tool for recovering files based on their headers, footers, and internal data structures.
- gimp: A tool for editing images 


Practice:

-  https://github.com/SubtleScope/steganography/tree/master
### 3) Cracking Protected files
- [JohnTheRipper](http://www.openwall.com/john/) : [Tutorial](https://www.youtube.com/watch?v=XjVYl1Ts6XI&pp=ygUYam9obiB0aGUgcmlwcGVyIHR1dG9yaWFs)
- [fcrackzip](https://www.kali.org/tools/fcrackzip/)
- [pdfcrack](https://www.kali.org/tools/pdfcrack/)

Example challenges: 
- https://ctftime.org/writeup/28379
- https://ctftime.org/writeup/27600
- https://ctftime.org/writeup/30165
- https://ctftime.org/writeup/19665
### 4) Audio Forensics

- [Audacity](http://sourceforge.net/projects/audacity/): Analyze sound files (mp3, m4a, whatever).
- [Sonic Visualizer](https://www.sonicvisualiser.org/) : This tool can be used to manipulate and find data hidden in different channels of an Audio file.

    - Example: https://kamransaifullah.medium.com/milkshake-stenography-challenge-solution-de046379bff5

- Audio Spectrograms: https://www.youtube.com/watch?v=rAGkm4pv44s

- [Wavsteg](https://github.com/ragibson/Steganography#WavSteg) : python3 tool that can hide data and files in wav files and can also extract data from wav files

- Morse Code: https://en.wikipedia.org/wiki/Morse_code
Conversion of Morse code from wav file: https://morsecode.world/international/decoder/audio-decoder-adaptive.html

- DTMF : https://en.wikipedia.org/wiki/DTMF
A tool to extract keys being pressed in the DTMF tone can be extracted using [this tool](https://github.com/ribt/dtmf-decoder).

More examples : 
- https://ctf-wiki.mahaloz.re/misc/audio/introduction/
- https://ctftime.org/writeup/38091
- https://ctftime.org/writeup/8835
### 5) Memory Forensics

- [Volatility](https://github.com/volatilityfoundation/volatility) [ For python3 : [volatility3](https://github.com/volatilityfoundation/volatility3) ]- Very popular memory forensic tool, a very good resource is the following:
    - [Part 1](https://westoahu.hawaii.edu/cyber/forensics-weekly-executive-summmaries/memory-ctf-with-volatility-part-1/),  links to further parts can be found on the same website.
    - Note: Volatility Framework had a major revision with Volatility3 , multiple guides available on the internet still refer to the older version i.e. Volatility2 . Keep that in mind :)

- [OfflineRegistryView](https://www.nirsoft.net/utils/offline_registry_view.html) : Tool for Windows that allows you to read offline Registry files from external drives.
- [Extundelete](http://extundelete.sourceforge.net/) : Used for recovering lost data from mountable images.
- [Rekall](https://github.com/google/rekall) : Memory Forensic Framework


**For practice : [Memlabs](https://github.com/stuxnet999/MemLabs)**

### 6) Network Forensics
**Wireshark** is a packet sniffer and analysis tool. It captures network traffic from ethernet, Bluetooth, wireless, etc.., and stores that data for offline analysis.

[Learn Wireshark](https://www.youtube.com/playlist?list=PLBf0hzazHTGPgyxeEj_9LBHiqjtNEjsgt)

**Some practice challenges**:

- Challenge 1: https://play.picoctf.org/practice/challenge/115?page=1&search=shar
- Challenge 2:
https://play.picoctf.org/practice/challenge/30?page=1&search=shar
- Challenge 3:
https://play.picoctf.org/practice/challenge/103?page=1&search=Triv
- Challenge 4:
https://play.picoctf.org/practice/challenge/237?page=1&search=WPA
- Challenge 5:
https://play.picoctf.org/practice/challenge/362?page=1&search=Pca
- Challenge 6:
https://play.picoctf.org/practice/challenge/32?page=1&search=web
----
Overall practice : 
- https://github.com/BYU-CSA/old-ctf-challenges/tree/master/forensics-steganography
- Solve as much challenges you could from **Picoctf** : https://play.picoctf.org/practice?category=4&page=1
## 2. OSINT

**OSINT**: Open source intelligence is the collection and analysis of data gathered from open sources like social media, news articles, company websites etc. to produce actionable intelligence.
Cyber criminals use OSINT to collect information on a target before attacking; also, OSINT can be used to help guess a user’s password.

### 1) **Sock Puppets**
Sock puppets, also known as research accounts, are online fictitious identities used to conceal the true identity of the OSINT investigator and to gain access to information that requires an account to access. Sock puppets are also created to isolate OSINT research, ensuring a separation between the personal and work lives of OSINT investigators.

This is OPTIONAL at introduction level, but a good practice!

How to create effective sock puppet, check
- https://web.archive.org/web/20210307173507/https://jakecreps.com/sock-puppets/
- [Art of the sock](https://www.secjuice.com/the-art-of-the-sock-osint-humint/)
- https://www.reddit.com/r/OSINT/comments/dp70jr/my_process_for_setting_up_anonymous_sockpuppet/
 

**Some Tools**:
- Fake Name Generator: https://www.fakenamegenerator.com/
- AI Generated face images: https://www.thispersondoesnotexist.com/

### 2) **Search Engines**
- Google
    - Advanced Google Search
    - Search Guide
- Yandex
- Baidu
- DuckDuckGo
- Bing

**Wayback Machine** : https://wayback-api.archive.org/

### 3) Image OSINT
Have an Image and need to gather information about it ? Has it been posted anywhere before? What other similar images are on the internet?

Tools:
- [Google Image Search](https://images.google.com/)
- [Yandex Image Search](https://yandex.com/images/)
- [Tinyeye Image Search](https://tineye.com/)

Example OSINT on street art: https://www.secjuice.com/street-art-in-osint-investigations/

### 4) Geography OSINT

Have to figure out where in the world you may be, using a photo of that location !

Tools:
- [Google Maps](https://www.google.com/maps) (another useful tool that it provides is the Streetview)
- [EarthCam](https://www.earthcam.com/): Webcams from around the world
- [N2YO](https://www.n2yo.com/): Satellite Tracker
- [Geoguessr](https://www.geoguessr.com/): browser-based geography game in which players are tasked to guess locations from Google Street View imagery.
- [PlonkIt](https://www.plonkit.net/guide): Very detailed guide to Geoguessing. 

### Fore more resources : https://www.osintdojo.com/resources/

### 5) Try some of the following challenges:
- [Sakura Room (TryHackMe)](https://tryhackme.com/room/sakura)
- [OhSINT room (TryHackMe)](https://tryhackme.com/room/ohsint)
- [SoMeSINT room (TryHackMe)](https://tryhackme.com/r/room/somesint)
- https://gralhix.com/list-of-osint-exercises/
- https://quiz.sector035.nl/