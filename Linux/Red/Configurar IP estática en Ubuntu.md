# Configurar IP estática en Ubuntu
---
Ver la información de red
````terminal
$ ifconfig -a
````

El archivo _.yaml_ contiene la informacion necesaria para aplicar la configuración de red del equipo.
````terminal
$ vim /etc/netplan/00-installer-config.yaml
````

````
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: false
      addresses: [192.168.1.xx/24]
      gateway4: 192.168.1.1
	  nameservers:
	    addresses: [8.8.8.8, 4.4.4.4]
````

````terminal
$ sudo netplan apply
````

Comprobamos que se han realizado los cambios
````terminal
$ ifconfig -a
````