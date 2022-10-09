# Find
```
[user@serverlinux ~]$ find <directory_path> <search_parameter>
```
```
[user@serverlinux ~]$ find / -iname "*.py"
```
| Argument | Description |
|:--------:| ----------- |
| -name, -iname | Quita los espacios en blanco |
| -type f/d/l | tipo de objeto file, dir, link |
| -empty, -size b, k, M, G | Tamaño del archivo (+100G) |
| -ctime, -mtime, -atime s,m,h,d,M | Tiempo de creación, modificación, acceso (+30d) |
| -user, -group | Usuarios y grupos especificos |
| -perm | Permisos especificos (775) |
| -and | Y |
| -or | O |
| -not | Inversa |
| -maxdepth | Máxima profundidad de recursión |
| -mindepth | Mínima profundidad de recursión |
| -exec | Ejecuta el -exec al resultado del find (como el xargs) |
| -ok | Lo mismo que -exec pero con confirmaci |