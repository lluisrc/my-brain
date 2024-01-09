### $?
Devuelve 0 si el comando anterior se ejecutó correctamente.
```
[user@serverlinux ~]$ mkdir test01
[user@serverlinux ~]$ echo "$?"
0
```
Devuelve 1 si el comando anterior no se ejecutó correctamente.
```
[user@serverlinux ~]$ ls /path/do/not/exist
[user@serverlinux ~]$ echo "$?"
1
```
Devuelve 127 si el comando anterior no existe.
```
[user@serverlinux ~]$ dfajsdlf
[user@serverlinux ~]$ echo "$?"
127
```

### /dev/null
Devuelve la salida a /dev/null (a nada) y la salida de errores la redirige a stdoutput
```
[user@serverlinux ~]$ echo "Hola" > /dev/null 2<&1
```

### Mostrar/Ocultar el cursor
Muestra el cursor
```
tput cnorm
```
Ocultar el cursor
```
tput civis
```
### rlwrap
Hace un historico de comandos para utilizar las fechas de arriba y abajo y cambiar de comando mas rapido
```
[user@serverlinux ~]$ rlwrap
```
### product_uuid
Este archivo muestra un identificador único que está asociado al hardware

Cuando hacemos un import de una vm se genera un nuevo product_uuid. A pesar que el disco sea el mismo el resto de hardware (CPU, mem, motherboard...) no son el mismo (new vm)

Para ver el product_uuid lanzamos el siguiente comando:
```
# cat /sys/class/dmi/id/product_uuid
```

### Silenciar el ruido del terminal al auto-completar
```terminal
vim /etc/inputrc
```
Descomentar el parámetro `set bell-style none`

### !$
Se refiere al último argumento del comando anterior

```terminal
mkdir hola
cd !$
```
