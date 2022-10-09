## $?
Imprime por pantalla el codigo de estado del comando anterior:

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