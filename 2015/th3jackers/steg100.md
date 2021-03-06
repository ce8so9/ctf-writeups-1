### Solved by superkojiman

The file has no extension, but a quick check with the file command shows it's a jpeg:

```
# file d30b7599498d0e8cf28f2cd9a7c9b9ba 
d30b7599498d0e8cf28f2cd9a7c9b9ba: JPEG image data, JFIF standard 1.01
```

Running strings on it reveals some interesting text at the end of the file:

```
K="KhtgduHjj"Guess?
```

Using outguess, I was able to extract the hidden message from the file, using KhtgduHjj as the key: 

```
# mv d30b7599498d0e8cf28f2cd9a7c9b9ba steg200.jpg
# outguess -k KhtgduHjj -r steg200.jpg msg.txt
Reading steg200.jpg....
Extracting usable bits:   40455 bits
Steg retrieve: seed: 146, len: 33
```

Reading the contents of the hidden message showed the following:

```
# cat msg.txt 
Jbhun_Hlbh_S0HhaQ_GU3_SyNnt0K_==
```

This wasn't the flag, but a ROT13 encrypted version of it. Decrypting it yields the flag: 

```
# python -c 'print "Jbhun_Hlbh_S0HhaQ_GU3_SyNnt0K_==".encode("rot13")'
Wouha_Uyou_F0UunD_TH3_FlAag0X_==
```

The flag is **flag{Wouha_Uyou_F0UunD_TH3_FlAag0X_==}**
