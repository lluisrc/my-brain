Vamos a importar una vm. Esta se encuentra en `C:\Users\lluis\OneDrive\Documentos\template_redhat92`

Una vez hemos importado la vm tenemos que:
- Cambiar el hostname
- Editar el fichero `/etc/hosts`
- Asignar una IP válida
- Cambiar el id de la máquina
- Registrar la VM a redhat

### Cambiar hostname
El formato del hostname se define de la siguiente manera `<hostname>-<4ºOctetoIP>` (Ej: redhat-test-103)
Para cambiar el hostname editamos el archivo `/etc/hostname` (requiere reinicio)

### Editar el fichero /etc/hosts
Con el siguiente comando editamos el archivo de resolución de nombres del sistema para añadir que el hostname resuelva a localhost

### Asignar una IP válida
En las máquinas virtuales se les asigna una IP a partir de la 100 (192.168.1.1XX)
```terminal
# nmcli connection edit ens33
nmcli> print ipv4
nmcli> remove ipv4.address
nmcli> set ipv4.addresses 192.168.1.1XX/24
nmcli> print ipv4
nmcli> save
nmcli> activate ens33
nmcli> quit
# nmcli connection down ens33 && nmcli connection up ens33
```
### Cambiar el id de la máquina
Cambiar el id de la máquina es importante porque la vm que importamos tiene un ID y estaríamos haciendo duplicación (requiere reinicio).
```
# rm -f /etc/machine-id
# systemd-machine-id-setup
```
### Registrar la VM a redhat
Para registrar la VM a redhat ejecutamos el siguiente comando
```
# subscription-manager register
```

El usuario y la contraseña de la plantilla es root root