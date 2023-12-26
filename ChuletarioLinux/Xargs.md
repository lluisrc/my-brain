La salida del comando anterior se utilizará como argumento en el parámetro de xargs
```terminal
[user@serverlinux ~]$ find . -name archivo.txt | xargs cat
[user@serverlinux ~]$ ls kernel* | xargs rm -f
```
