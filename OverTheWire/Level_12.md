## Bandit Level 12 -> Level 13

## Level Goal

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv

## Helpful Reading Material

1. [Hex dump on Wikipedia](http://en.wikipedia.org/wiki/Hex_dump)

## Solution

1. Passing this level need to know the usage of command 'xxd, gzip, bzip2, tar'
Bacause the file need to be uncompressed repeatedly.
I uncompressed and created a new file each step of the way by hand, it is tiring but I finally got the answer

the details followed are complicated:

```
bandit12@melinda:~$ ls
data.txt
bandit12@melinda:~$ file data.txt
data.txt: ASCII text
bandit12@melinda:~$ mkdir /tmp/stw
bandit12@melinda:~$ cd /tmp/stw
bandit12@melinda:/tmp/stw$ xxd -r ~/data.txt > data.txt
bandit12@melinda:/tmp/stw$ file data.txt
data.txt: gzip compressed data, was "data2.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
 
bandit12@melinda:/tmp/stw$ zcat data.txt > dataNew
bandit12@melinda:/tmp/stw$ ls
dataNew  data.txt
bandit12@melinda:/tmp/stw$ file dataNew
dataNew: bzip2 compressed data, block size = 900k
bandit12@melinda:/tmp/stw$ bzip2 -d dataNew
bzip2: Can't guess original name for dataNew -- using dataNew.out
bandit12@melinda:/tmp/stw$ ls
dataNew.out  data.txt
bandit12@melinda:/tmp/stw$ file dataNew.out
dataNew.out: gzip compressed data, was "data4.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
 
bandit12@melinda:/tmp/stw$ zcat dataNew.out > evenNewer
bandit12@melinda:/tmp/stw$ ls
dataNew.out  data.txt  evenNewer
bandit12@melinda:/tmp/stw$ file evenNewer
evenNewer: POSIX tar archive (GNU)
bandit12@melinda:/tmp/stw$ tar -xvf evenNewer
data5.bin
bandit12@melinda:/tmp/stw$ file data5.bin
data5.bin: POSIX tar archive (GNU)
 
bandit12@melinda:/tmp/stw$ tar -xvf data5.bin
data6.bin
bandit12@melinda:/tmp/stw$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@melinda:/tmp/stw$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
 
bandit12@melinda:/tmp/stw$ ls
data5.bin  data6.bin.out  dataNew.out  data.txt  evenNewer
bandit12@melinda:/tmp/stw$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)
bandit12@melinda:/tmp/stw$ tar -xvf data6.bin.out
 
data8.bin
bandit12@melinda:/tmp/stw$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
 
bandit12@melinda:/tmp/stw$ zcat data8.bin > lost
bandit12@melinda:/tmp/stw$ ls
data5.bin  data6.bin.out  data8.bin  dataNew.out  data.txt  evenNewer  lost
bandit12@melinda:/tmp/stw$ file lost
lost: ASCII English text
bandit12@melinda:/tmp/stw$ cat lost
The password is <strong>8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL</strong>

