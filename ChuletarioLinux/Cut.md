Recorta la salida con el formato deseado.
```
[user@serverlinux ~]$ echo "Hola-Mundo-Como-Estás" | cut -d "-" -f2
```
Mundo

| Argument | Description |
|:--------:| ----------- |
| -f | fields |
| -c | characters |
| -d | delimiter |