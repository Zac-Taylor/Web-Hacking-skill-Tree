## Bandit Level 19 -> Level 20

## Level Goal

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used to setuid binary.

## Helpful Reading Material

1. [setuid on Wikipedia](http://en.wikipedia.org/wiki/Setuid)

## Solution

```
bandit19@melissa:~$ ls
bandit20-do
bandit19@melissa:~$ ./bandit20-do
Run a command as another user.
Example: ./bandit20-do id
bandit19@melissa:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11020(bandit20),11019(bandit19)
bandit19@melissa:~$ ./bandit20-do whoami
bandit20
bandit19@melissa:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```


