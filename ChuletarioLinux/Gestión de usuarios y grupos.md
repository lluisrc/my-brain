### Crear usuario
```terminal
[root@serverlinux ~]# useradd lroca -d /home/lroca -s /bin/bash
```
| Argument | Description |
|:--------:| ----------- |
| -d | define el directorio home del usuario |
| -s | define la shell |
| -g | define el grupo como primario |
| -G | define el grupo secundario |


### Crear grupo
```terminal
[root@serverlinux ~]# groupadd docker
```

### Añadir usuario a grupo
```terminal
[root@serverlinux ~]# usermod lroca -aG docker
```
| Argument | Description |
|:--------:| ----------- |
| -a | append (sin la -a, remplaza) |
| -G | define el grupo como secundario |
| -g | define el grupo como primario |

### Quitar usuario a grupo
```terminal
[root@serverlinux ~]# gpasswd nginx -d lroca
Removing user lroca from group nginx
```
| Argument | Description |
|:--------:| ----------- |
| -d, --delete | Quita el grupo al usuario |

### Crear usuario de forma atendida
```terminal
adduser
```