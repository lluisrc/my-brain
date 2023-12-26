Edita el texto de un archivo.
```
[user@serverlinux ~]$ sed -i 's/Microsoft Windows/GNU Linux/2' fichero.txt
```
s sustitución<br>
/ delimitadores
- primera posición del delimitador es el patrón de búsqueda
- segunda posición del delimitador es la cadena de remplazo
- tercera posición del delimitador es el numero de apariciones por línea en la que ará la sustitución, en este caso 2. Utilizamos 'g' para todas las apariciones.


Podemos indicar que línea especifica debe acutar
```
[user@serverlinux ~]$ sed '5 s/Microsoft Windows/GNU Linux/2' fichero.txt
```

Podemos indicar un rango de lineas donde debe acutar
```
[user@serverlinux ~]$ sed '5,10 s/Microsoft Windows/GNU Linux/2' fichero.txt
```

Podemos eliminar una fila de un fichero
```
[user@serverlinux ~]$ sed '5d' fichero.txt
```

Podemos eliminar un rango de filas de un fichero
```
[user@serverlinux ~]$ sed '5,10d' fichero.txt
```

-i se aplica los cambios en el archivo, en caso contrario solo se ve reflejado en el output
```
[user@serverlinux ~]$ sed -i 's/^que .*$/el contenido de la línea ha sido reemplazado/' sedexamples.txt
```

> El carácter \ convierte el siguiente caracter en str. Ejemplo --> \/<br>
> / será un string y no un limitador

https://www.tutorialspoint.com/unix/unix-regular-expressions.htm
