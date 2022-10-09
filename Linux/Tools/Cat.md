# Cat
---
Leer un archivo sin comentarios ni espacios
````terminal
$ cat <archivo> | grep -v "#" | sed -e "/^$/d"
````