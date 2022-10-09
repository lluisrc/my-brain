# Administración de usuarios y grupos
### Crear usuario
```
[root@serverlinux ~]# useradd lroca
```
> El parámetro -d se usa para crear el usuario sin su directorio en el /home

### Modificar usuario
usermod

### Crear grupo
```
[root@serverlinux ~]# groupadd docker
```
### Asignar grupos a usuarios
```
[root@serverlinux ~]# usermod -aG docker lroca
```
| Argument | Description |
|:--------:| ----------- |
| -a | append (sin la -a, remplaza) |
| -G | define el grupo como secundario |
| -g | define el grupo como primario |