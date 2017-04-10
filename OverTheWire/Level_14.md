## Bandit Level 14 -> Level 15

## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
Commands you may need to solve this level

ssh, telnet, nc, openssl, s_client, nmap

## Helpful Reading Material

1. [How the Internet works in 5 minutes (YouTube)](https://www.youtube.com/watch?v=7_LPdttKXPc) (Not completely accurate, but good enough for beginners)
2. [IP Addresses](http://computer.howstuffworks.com/web-server5.htm)
3. [IP Address on Wikipedia](http://en.wikipedia.org/wiki/IP_address)
4. [Localhost on Wikipedia](http://en.wikipedia.org/wiki/Localhost)
5. [Ports](http://computer.howstuffworks.com/web-server8.htm)
6. [Port (computer networking) on Wikipedia](http://en.wikipedia.org/wiki/Port_(computer_networking))

## Solution

```
bandit14@melissa:~$ telnet localhost 30000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
 
Connection closed by foreign host.
```


