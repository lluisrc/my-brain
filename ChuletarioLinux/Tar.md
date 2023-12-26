Comprimir archivos
| Parámetro | Descripción |
|:--------:|-------------|
| c | crear un nuevo archivo .tar |
| v | muestra una descripción detallada del progreso de la compresión |
| f | nombre del archivo |
| z | compresión .gzip |
| j | compresión .bz2 |
| r | agregar archivo a .tar |

```terminal
[root@serverlinux ~]# tar -cvf sampleArchive.tar /home/sampleArchive
```

Descomprimir archivo
| Parámetro | Descripción |
|:--------:|-------------|
| x | descomprime el archivo |
| C | extraer a un directorio diferente |
```
[root@serverlinux ~]# tar -xvf sampleArchive.tar
```

Descomprimir archivo único
```
[root@serverlinux ~]# tar -xvf sampleArchive.tar example.sh
```

Con wildcard
```
[root@serverlinux ~]# tar -xvf sampleArchive.tar --wildcards '*.jpg'
```

Verificar tar
| Parámetro | Descripción |
|:--------:|-------------|
| t | verificar el archivo |
```
[root@serverlinux ~]# tar -tvf sampleArchive.tar