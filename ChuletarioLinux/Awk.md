Imprime la primera columna (por defecto el delimitador es el espacio)
```terminal
[user@serverlinux ~]$ ps | awk '{print $1}'
```
    
Imprime la primera columna pero NO la primera fila, NR --> Number Row
```terminal
[user@serverlinux ~]$ ps | awk 'NR>1{print $2}'
```

Cambiar el delimitador -F ":"
```terminal
[user@serverlinux ~]$ cat /etc/passwd | awk -F ":" '{print $1}'
```

Mostrar coincidencias (como un grep)
```terminal
[user@serverlinux ~]$ cat fichero.txt | awk '/^tmpfs/ {print}'
```

Contar el numero de líneas (como un wc -l)
```terminal
[user@serverlinux ~]$ cat fichero.txt | awk '{print NR}' /etc/shells
```

Imprimir la primera/rango linea
```terminal
[user@serverlinux ~]$ cat fichero.txt | awk 'NR==1{print $0}'
[user@serverlinux ~]$ cat fichero.txt | awk 'NR>2{print $0}'
[user@serverlinux ~]$ cat fichero.txt | awk 'NR==2, NR==4 {print $0}'
```