
```
[user@linuxserver ~]$ ss -tulwn | grep LISTEN
```

| Parámetro | Descripción |
|:--------:|-------------|
| -a | Display both listening and non-listening (for TCP this means established connections) sockets |
| -t | Show only TCP sockets on Linux |
| -u | Display only UDP sockets on Linux |
| -l | Show listening sockets. For example, TCP port 22 is opened by SSHD server |
| -p | List process name that opened sockets |
| -n | Don’t resolve service names i.e. don’t use DNS |
| -w | Display RAW sockets |

Ver todos los puertos TCP/UDP
```
[user@linuxserver ~]$ ss -t -a
[user@linuxserver ~]$ ss -u -a
```

Ver Puertos abiertos
```
[user@linuxserver ~]$ ss -o state established '( dport = :ssh or sport = :ssh )'
```