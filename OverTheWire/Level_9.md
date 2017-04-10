## Bandit Level 9 -> Level 10

## Level Goal

The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several '=' characters.

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd


## Solution

bandit9@melissa:~$ ls
data.txt
bandit9@melissa:~$ strings data.txt | grep '='
========== the
R=ev2,
NF=!^
M5Q=
========== password
TuI@=
========== iss
c       =$
w=RO
eD=p
jR=JlB
G========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
:=*1p
KA=%