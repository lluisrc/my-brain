# Tcpdump
Este comando captura los paquetes que viajan por la red. Mas tarde, estos paquetes se pueden analizar con wireshark
```
[user@serverlinux ~]$ tcpdump <argumentos>
```

| Opciones | Description |
|:--------:| ----------- |
| -w | Donde output podemos poner el nombre/ubicación donde se guarda el archevo |
| host \<host\> | Analiza los paquetes entrantes  y salientes del host |
| port \<nº puerto\> | Filtra los paquetes y caputura solo los del puerto definido |
| -v, -vv | Muestra más detalle en la salida del comando |
| src | Solo captura los paquetes de origen en la comunicación |
| dest | Solo captura los paquetes de destinatario en la comunicación |
| -i | Para que escuche por una interfaz de red especifica |
Más info en --> https://danielmiessler.com/study/tcpdump/