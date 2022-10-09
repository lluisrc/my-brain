````
ESCANEO RÁPIDO
[root@linuxserver ~ ]# nmap -p- --open -T5 -v -n <ip>

ESCANEO SUPER RAPIDO
[root@linuxserver ~ ]# nmap -sS --min-rate 5000 -p- --open -vvv -n -Pn <ip> -oG allPorts

[root@linuxserver ~ ]# nmap -sC -sV -p<port> <ip> -oN <output-file> 
````

	