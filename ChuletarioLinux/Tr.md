Remplaza los characters de la salida del comando anterior con el formato deseado.<br>
La primera opción indica que quieres reemplazar y la segunda a qué.
```terminal
[user@serverlinux ~]$ echo "Hola mundo!" | tr "[OPCIONES]" "[OPCIONES]"
[user@serverlinux ~]$ echo "Hola mundo!" | tr "[:lower:]" "[:upper:]"
```
| Argument | Description |
|:--------:| ----------- |
| -c | Contrario, el que no sea... |
| -d | Delete (elimina los caracteres del set1) |
| -s | Sustituye las secuencias de repetidas occurrencias |

| Opciones | Description |
|:--------:| ----------- |
| \[:lower:] | Todas las mayusculas |
| \[:upper:] | Characters |
| \[:digit:] | Delimiter |
| \[:space:], [:blank:] | Todos los espacios en blanco horizontales |
| \[:alpha:] | Todas las letras |
| \[:alnum:] | Todas las letras y numeros |


Todas las minusculas a mayusculas
```terminal
[user@serverlinux ~]$ echo "Hola mundo!" | tr "[:lower:]" "[:upper:]"
```
Todo lo que no contecga A me lo pones a t
```terminal
[user@serverlinux ~]$ echo "Abc123d56E" | tr -c 'A' 't'
```
Las secuencias de ' ' me las sustituyes por un ' ' 
```terminal
[user@serverlinux ~]$ echo "GNU     \    Linux" | tr -s ' '
```
