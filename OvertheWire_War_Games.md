# OvertheWire War Games

## ssh bandit2@bandit.labs.overthewire.org -p 2220

## Lvl0 - Lvl1

**The password for the next level is stored in a file called readme located in the home directory**

```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
--------------

## Lvl1 - Lvl2

**The password for the next level is stored in a file called - located in the home directory**
```
cat ./- : CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
--------------


## Lvl2 - Lvl3

**The password for the next level is stored in a file called spaces in this filename located in the home directory**

```
cat “spaces in this filename” : UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
--------------

## Lvl3 - Lvl4

**The password for the next level is stored in a hidden file in the inhere directory**

```
cat .hidden : pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```
--------------

## Lvl4 - Lvl5 

**The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.**

```
file inhere/* : koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
--------------

## Lvl5 -Lvl6

**The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:**

 - human-readable
 - 1033 bytes in size
 - not executable

```
find ./* -type f -size 1033c ! -executable : DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```
--------------

## Lvl6 -Lvl7

**The password for the next level is stored somewhere on the server and has all of the following properties:**

 - owned by user bandit7
 - owned by group bandit6
 - 33 bytes in size

```
find / -type f -user bandit7 -group bandit6 -size 33c 2> /dev/null: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```
--------------

## Lvl7 - Lvl8

**The password for the next level is stored in the file data.txt next to the word millionth**

```
cat data.txt | grep -i millionth : cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

--------------

## Lv8 - Lvl9

**The password for the next level is stored in the file data.txt and is the only line of text that occurs only once**

```
sort data.txt | uniq -u : UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
--------------

## Lvl9 - Lvl10


**The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.**

```
strings data.txt | grep "=" : truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

--------------

## Lvl10 - Lvl11

**The password for the next level is stored in the file data.txt, which contains base64 encoded data**

```
base64 -d data.txt : IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

--------------


## Lvl11 - Lvl12

**The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions. Reference Rot13**

```
echo "Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh" | tr '[A-Za-z]' '[N-ZA-Mn-za-m]' : 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

--------------


## Lvl12 - Lvl13

**The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)**

```
cp data.txt /tmp/dan123/
```
```
xxd -r dan.txt new_dan.txt
```

--------------


## Lvl13 - Lvl14

****

```

```

--------------


## Lvl14 - Lvl15

****

```

```

--------------


## Lvl15 - Lvl16

****

```

```

--------------


## Lvl16 - Lvl17

****

```

```

--------------


## Lvl17 - Lvl18

****

```

```

--------------


## Lvl18 - Lvl19

****

```

```

--------------


## Lvl19 - Lvl20

****

```

```

--------------
