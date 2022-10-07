# Crear una VM
---
Hacemos un clon de la plantilla.
Lo guradamos el `c:\src\vm\`
El nombre empezará con "_centos_" (ejemplo: _centos_apache1_)
La ip es estática y empieza por _192.168.1.2xx_
````terminal
$ nmcli connection edit ens33
nmcli> print
nmcli> set ipv4.method manual
nmcli> set ipv4.dns 8.8.8.8
nmcli> set ipv4.addresses 192.168.1.2xx/24
nmcli> set ipv4.gateway 192.168.1.1
nmcli> print
nmcli> save
nmcli> quit
$ nmcli connection down ens33
$ nmcli connection up ens33
````
Vinculamos el dns con la ip estática y el nombre de la máquina
Cambiamos el hostname con el nombre de la máquina
`vim /etc/hostname` y `vim /etc/host bal bal`