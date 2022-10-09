# Awk
Imprime la primera columna (por defecto el delimitador es el espacio)
```
[user@serverlinux ~]$ ps | awk '{print $1}'
```
    
Imprime la primera columna pero NO la primera fila, NR --> Number Row
```
[user@serverlinux ~]$ ps | awk 'NR>1{print $2}'
```

Cambiar el delimitador -F ":"
```
[user@serverlinux ~]$ cat /etc/passwd | awk -F ":" '{print $1}'
```

Mostrar coincidencias (como un grep)
```
[user@serverlinux ~]$ cat fichero.txt | awk '/^tmpfs/ {print}'
```

Contar el numero de líneas (como un wc -l)
```
[user@serverlinux ~]$ cat fichero.txt | awk '{print NR}' /etc/shells
```

Imprimir la primera/rango linea
```
[user@serverlinux ~]$ cat fichero.txt | awk 'NR==1{print $0}'
[user@serverlinux ~]$ cat fichero.txt | awk 'NR>2{print $0}'
[user@serverlinux ~]$ cat fichero.txt | awk 'NR==2, NR==4 {print $0}'
```