## Bandit Level 20 -> Level 21

## Level Goal

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: To beat this level, you need to login twice: once to run the setuid command, and once to start a network daemon to which the setuid will connect.

NOTE 2: Try connecting to your own network daemon to see if it works as you think

## Commands you may need to solve this level

ssh, nc, cat

## Solution

bandit20@melinda:~$ ls
suconnect
bandit20@melinda:~$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the
correct password from the other side, the next password is transmitted back.
 
#In one shell do:
bandit20@melinda:~$ nc -l 3222
 
#In another shell do:
bandit20@melinda:~$ ls
suconnect
bandit20@melinda:~$ ./suconnect 3222
 
#When the connection is made, go back to the first shell, and paste the password in netcat.
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
 
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password
```

