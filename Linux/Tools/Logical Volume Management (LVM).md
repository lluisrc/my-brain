# Logical Volume Management
Creo que pasa lo siguiente:
- Del disco haces la particion
- De la partición la haces phisical volumes
- del phisical volume lo añades al volume grupo
- del vol grupo haces logicals volumes y estos están montados los puntos de montaje
<img src="https://aws1.discourse-cdn.com/business5/uploads/manageiq/original/1X/fbf44336300273250f26cc06493a4d5d136aa5f0.png">
 
Para listar de forma detallada los grupos de volumenes `vgdisplay -v`
Para listar volumentes lógicos  `lvdisplay -v`
Para listar los volumentes físicos `pvdisplay -v`

Create volum grup a partir de un phisical volume, coje la partición para hacer el phisical group
````terminal
# vgcreate <nombre_grupo> <partición>
````
Extender volum group:
````termianl
# vgextend <nombre_grupo> <partición>
````
Crear volumenes lógicos:
````teminal
# lvcreate --size 10g -n <nombre_fs> <nombre_grupo>
````

```
pvcreate /dev/sdc  
vgcreate VolGroup01 /dev/sdc  

lvcreate -l 100%FREE -n cassandra VolGroup01

lvdisplay  

mkfs.xfs /dev/VolGroup01/cassandra  
vim /etc/fstab
```

Deshacer
```
umount /opt/cassandra

lvremove /dev/VolGroup00/cassandra

vgremove cassandra
```