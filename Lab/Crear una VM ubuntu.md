Vamos a importar una vm. Esta se encuentra en `C:\Users\lluis\OneDrive\Documentos\template_ubuntu2204`

Una vez hemos importado la vm tenemos que:
- Cambiar el hostname
- Editar el fichero `/etc/hosts`
- Asignar una IP válida
- Cambiar el id de la máquina

### Cambiar hostname
El formato del hostname se define de la siguiente manera `<hostname>-<4ºOctetoIP>` (Ej: redhat-test-103)
Para cambiar el hostname editamos el archivo `/etc/hostname` (requiere reinicio)

### Editar el fichero /etc/hosts
Con el siguiente comando editamos el archivo de resolución de nombres del sistema para añadir que el hostname resuelva a localhost

### Asignar una IP válida
Editamos el fichero `/etc/netplan/00-installer-config.yaml`
Aplicamos la configuración con el siguiente comando
```terminal
$ sudo netplan apply
```
### Cambiar el id de la máquina
Cambiar el id de la máquina es importante porque la vm que importamos tiene un ID y estaríamos haciendo duplicación (requiere reinicio).
```
# rm -f /etc/machine-id
# systemd-machine-id-setup
```

El usuario y la contraseña de la plantilla es lroca lroca y root root