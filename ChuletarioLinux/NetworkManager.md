NetworkManager es un servicio para configurar la red
```
[root@linuxserver ~]# systemctl status NetworkManager
[root@linuxserver ~]# systemctl start NetworkManager
[root@linuxserver ~]# systemctl stop NetworkManager
[root@linuxserver ~]# systemctl restart NetworkManager
[root@linuxserver ~]# systemctl enable NetworkManager
```
Para ver las conexiones configuradas
```
[root@linuxserver ~]# nmcli connection show
```

Para añadir nueva conexión
```
[root@linuxserver ~]# nmcli con add con-name eth0 ifname ens192 type ethernet ip4 192.168.100.25/24
```

Para editar una conexión
```
[root@linuxserver ~]# nmcli connection edit ens192
nmcli> set connection.autoconnect yes
nmcli> set ipv4.method manual
nmcli> set ipv4.addresses 192.168.253.11/24
nmcli> set ipv4.gateway 192.168.253.254
nmcli> set ipv4.dns 192.168.253.61,192.168.253.62
nmcli> set ipv4.dns-search riu.net
nmcli> set ipv6.method disabled
nmcli> remove connection.permissions
nmcli> remove ipv6.addr-gen-mode
nmcli> save
nmcli> activate ens192
nmcli> quit
```
Modify va a editar el parámetro que estemos especificando sobreescribiendo la configuración previa (machaca lo antiguo para setear lo nuevo)
```terminal
[root@linuxserver ~]# nmcli connection modify ens192 ipv4.addresses 192.168.253.11/24
```

Para eliminar una conexión
```
[root@linuxserver ~]# nmcli connection delete eth0
```

Para reiniciar la tarjeta de red
```
[root@linuxserver ~]# nmcli networking off && nmcli networking on
```

Sobrescribe los parámetros de configuración
```
[root@linuxserver ~]# nmcli connection modify <device_name> ipv4.addresses '192.168.247.43/24'
```