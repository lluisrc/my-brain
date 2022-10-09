# /dev/null
Devuelve la salida a /dev/null (a nada) y la salida de errores la redirige a stdoutput
```
[user@serverlinux ~]$ echo "Hola" > /dev/null 2<&1
```