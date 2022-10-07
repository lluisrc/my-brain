# Configurar IP estática en CentOS
---
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
> Para eliminar una dirección ip estatica y que pase a ser dinámica: `remove ipv4.address`