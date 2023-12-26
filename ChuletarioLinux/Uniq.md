El binario uniq sirve para obtener los elementos únicos de una lista
```
[user@linuxserver ~]$ cat dias-semana.txt
Lunes
Martes
Martes
Miercoles
Jueves
Jueves
Jueves
Viernes
viernes
Sabado
Domingo
Domingo
Domingo
```

```
[user@linuxserver ~]$ cat dias-semana.txt | uniq
Lunes
Martes
Miercoles
Jueves
Viernes
viernes
Sabado
Domingo
```

Con el parámetro `-i` lo hace sin key sensitive