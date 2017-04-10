## Bandit Level 15 -> Level 16

## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -quiet and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

## Commands you may need to solve this level

ssh, telnet, nc, openssl, s_client, nmap

## Helpful Reading Material

1. [Secure Socket Layer/Transport Layer Security on Wikipedia](http://en.wikipedia.org/wiki/Secure_Socket_Layer)
2. [Testing SSL with commandline tools(https://web.archive.org/web/20070512053927/http://advosys.ca/viewpoints/2006/08/testing-ssl-with-command-line-tools/)

## Solution

Passing this level need to know the usage of s_client of command openssl.
and option -quiet dont print session and ca, meanwhile -ign_eof is opened to be connected when the output reach eof

```
bandit15@melinda:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
depth=0 /CN=melinda.labs.overthewire.org
verify error:num=18:self signed certificate
verify return:1
depth=0 /CN=melinda.labs.overthewire.org
verify return:1
---
Certificate chain
0 s:/CN=melinda.labs.overthewire.org
i:/CN=melinda.labs.overthewire.org
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICyjCCAbICCQDE6DxysXt56TANBgkqhkiG9w0BAQUFADAnMSUwIwYDVQQDExxt
ZWxpc3NhLmxhYnMub3ZlcnRoZXdpcmUub3JnMB4XDTEyMDUxMDIxMzYzOVoXDTIy
MDUwODIxMzYzOVowJzElMCMGA1UEAxMcbWVsaXNzYS5sYWJzLm92ZXJ0aGV3aXJl
Lm9yZzCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAL85VFz7tV/45RID
5x804dSKyvmZH62lOjAg0NhW7Kbc9L6mmq3EVd4As/kupXYs0d7hCiMjJri0X2e8
GTM+nysxZLTR1qa2j/KOzQ7FgQ4vp4R4JQZP6ofhNPvBybh6BwYE5hFzRARK9Y3x
+dr3ZefeAE7Ea1k6NzH7p6HAtpkG36SD6GbhLV9HFhwOCwBWGPnXPfXA/2XBdZzY
/h6FWrxZPqdALjy8dCeRlNPqG7dD8CIWK4dpBGudxfyXiki5YfwOirotEWjI1E/C
JK2/jWT7tYLIrVKzOF0dwDWYxNMRnwn5+S2F2/AERSRBlwrtMb6jJf+g2pU27eAe
3xvtJs8CAwEAATANBgkqhkiG9w0BAQUFAAOCAQEAtDKEX9gWmEyKqkhPN1L+wjEi
M2HH/XMgDxHrqWgy0Xl9gznuvM0pkOEXUOKWkfKDQfskk8cbgqn0hEvaX7AKrNL4
Nbm1JD+hUSSFtW3sxmv+aHkdEz6H70oUp712wP2Hu3DF7paVSPC5yB1vqoNYmHX/
J9CwqptVj+dLaDeY+ayzEwOuaEcd+cpP4OTbMLy0SuKLONr1+NaA5IPaVE/XOmlE
wW7zNRcJ3kxnvsHrqF4ZeYPBLNmhDT3ZD4qso+JiL9lme5YbP7+dCQo5Oa1AT7Dz
UmKZhWQTLsnI6Eyl8NwLnxiSkIOUigN6WF8bnd1F9FVKfmjQDSjBJHGqTE4Trg==
-----END CERTIFICATE-----
subject=/CN=melinda.labs.overthewire.org
issuer=/CN=melinda.labs.overthewire.org
---
No client certificate CA names sent
---
SSL handshake has read 1436 bytes and written 229 bytes
---
New, TLSv1/SSLv3, Cipher is DHE-RSA-AES256-SHA
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: zlib compression
Expansion: zlib compression
SSL-Session:
Protocol  : TLSv1
Cipher    : DHE-RSA-AES256-SHA
Session-ID: 5AED820CF694E077E4F590C9089FC77A050DC3A3BBCE7F383B811CBD4937DAC9
Session-ID-ctx:
Master-Key: 201FB305DD48B3D4746DA988FD88B0EF939A766A393DFED1D9184DA6BD41B28F4ABDF06AE23DA7B0DEFF0329C69499E8
Key-Arg   : None
TLS session ticket:
0000 - b4 b5 f0 bf 88 14 bc 85-59 9b e6 22 ea f3 7f a1   ........Y.."....
0010 - 61 8a 25 48 a4 08 cb 5c-f0 2d 8a 97 b1 78 c3 eb   a.%H...\.-...x..
0020 - 14 6b 41 99 71 5e 62 6b-bf 6a 17 18 82 cc 69 1a   .kA.q^bk.j....i.
0030 - d5 a3 fd 08 97 8c b8 3a-d7 52 7c 01 31 eb c8 be   .......:.R|.1...
0040 - 09 a0 fd 58 cc aa d9 98-51 53 71 98 7d 8f 92 78   ...X....QSq.}..x
0050 - 00 8c d3 1d b0 57 df 70-0a af 92 44 6c b8 5e 85   .....W.p...Dl.^.
0060 - 1f e1 87 fd c6 da db bd-35 da 89 a0 b9 da fe 37   ........5......7
0070 - 0f 5b 4e d9 96 16 3b 7e-6b fb 0f 42 51 67 5f d9   .[N...;~k..BQg_.
0080 - 11 9a 8d a3 95 2a 9b d1-f6 9b ce 2c 55 62 92 4b   .....*.....,Ub.K
0090 - a8 89 b1 9f 8a b8 f7 6b-b7 65 2d e4 7e 52 6b 6c   .......k.e-.~Rkl
 
Compression: 1 (zlib compression)
Start Time: 1363810708
Timeout   : 300 (sec)
Verify return code: 18 (self signed certificate)
---
BfMYroe26WYalil77FoDi9qh59eK5xNr
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd
 
read:errno=0
```

