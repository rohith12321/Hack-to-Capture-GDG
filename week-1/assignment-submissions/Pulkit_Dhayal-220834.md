## LEVEL  0->1
usin ssh to connect to port 2220 with username as 'bandit0' and password as 'bandit0' only.
```bash
password  : ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```
## LEVEL  1->2
file is hidden so we first have to use the ls with proper arguments and then the file name is '-'
```bash
password : 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

## LEVEL 2->3
file has spaces in it
```bash 
passowrd : MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

## LEVEL 3->4
file is in the directory inhere and is hidden 
```bash
password : 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
## LEVEL 4->5
10 files are there we need to find the flag since one contain the flag. using file command we can see the type of file
```bash
password : 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

## LEVEL 5->6
need to use the find command to set the specification of the file which contain the password
```bash
password : HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

## LEVEL 6->7
we have to find a file with user=bandit7  and group=bandit6 in the server with size=33 bytes .. use the find command with -user -group -size arguments
```bash
password : morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

## LEVEL 7->8
grep command question 
```bash
password : dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

## LEVEL 8->9
we need to use sort before applying uniq -u for uniqe line since uniq need lines to be adjacent thats why it need to be sorted
```bash
password : 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

## LEVEL 9->10
strings command was use and then piping for grep command
```bash
password : FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
## LEVEL 10->11
base64 command usage for decoding
``` bash
password : dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## LEVEL 11-12
the data iss ROT13 encoded we can decode using tr as
```bash 
>> tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt  // string to string match 
password : 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

## LEVEL 12->13
look at the hex dump and look for headers 
1. our first compressed hex dump says "1f8b 0808" --> which matches with the gzip header \x1F\x8B\x08 so it is gzip compressed file and need to rename with proper file type .gz so that we can decompress
2. now "425a 6839" is the first bytes ofthe gzip decompressed file which matches to BZ = 425a and h = 68 (version 2) s it is .bz2 file. 
3. again we see the hex dump and it tells it is a gzip comppressed file so we decomppress it.
4. in hex dump we see there is a file name so we use tar to extract it and again we find the same and do the same extraction.
5. now we have a bzip2 and again we need to do extraction and its gzip
```bash
password : FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

## LEVEL 13->14
```bash
 ssh key:
 -----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
-----END RSA PRIVATE KEY-----

password : MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

## LEVEL 14->15
need to connect to port 30000 and submit the previous password
```bash
password : 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```




