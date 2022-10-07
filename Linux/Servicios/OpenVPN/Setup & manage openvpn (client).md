To install:
````
[root@linux ~ ]# sudo apt install openvpn
````

To manage:
````
PARA ESTABLECER CONEXION CON LA VPN
[root@linux ~ ]# sudo openvpn --config ${fichero.ovpn}
[root@linux ~ ]# sudo openvpn --config ${fichero.ovpn} & // segundo plano

PARA CORTAR CONEXION CON LA VPN
**Si está en primer plano --> Ctrl + C
**Si está en segundo plano:
[root@linux ~ ]# jobs //para mirar los jobs en segundo plano
[root@linux ~ ]# fg %<nº job> // para traer a primer plano el proceso
(Ctrl + C)

OTRA OPCIÓN PARA CORTAR LA CONEXIÓN CON LA VPN ES
[root@linux ~ ]# sudo killall openvpn //elimina todos los procesos openvpn


````