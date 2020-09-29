OvertheWire War Games
ssh bandit2@bandit.labs.overthewire.org -p 2220

## Lvl0 - Lvl1

**The password for the next level is stored in a file called readme located in the home directory**

```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
--------------

## Lvl1 - Lvl2

**The password for the next level is stored in a file called - located in the home directory**
```
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9: cat ./-
```
--------------


## Lvl2 - Lvl3

**The password for the next level is stored in a file called spaces in this filename located in the home directory**

```
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK: cat “spaces in this filename”
```
--------------

## Lvl3 - Lvl4

**The password for the next level is stored in a hidden file in the inhere directory**

```
pIwrPrtPN36QITSp3EQaw936yaFoFgAB: cat .hidden
```
--------------

## Lvl4 - Lvl5 

**The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.**

```
koReBOKuIDDepwhWk7jZC0RTdopnAYKh:file inhere/* 
```
--------------

## Lvl5 -Lvl6

**The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:**

 - human-readable
 - 1033 bytes in size
 - not executable

```
DXjZPULLxYr17uwoI01bNLQbtFemEgo7:find ./* -type f -size 1033c ! -executable
```
--------------

## Lvl6 -Lvl7

**The password for the next level is stored somewhere on the server and has all of the following properties:**

 - owned by user bandit7
 - owned by group bandit6
 - 33 bytes in size

```
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs:find / -user bandit7 -group bandit6 -size 33c
```
--------------

## Lvl7 - Lvl8

**The password for the next level is stored in the file data.txt next to the word millionth**

```
cvX2JJa4CFALtqS87jk27qwqGhBM9plV:cat data.txt | grep -i millionth
```

--------------

## Lv8 - Lvl9

**The password for the next level is stored in the file data.txt and is the only line of text that occurs only once**

```
```

--------------

## Lvl9 - Lvl10

****

```
```

--------------
