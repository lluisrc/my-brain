### Análisis del entorno LVM
Escanear Volúmenes Físicos
```
[user@linuxserver ~]$ pvscan
[user@linuxserver ~]$ pvdisplay -vv
```
Escanear Grupos
```
[user@linuxserver ~]$ vgscan
[user@linuxserver ~]$ vgdisplay -vv
```
Escanear Volúmenes
```
[user@linuxserver ~]$ lvscan
[user@linuxserver ~]$ lvdisplay -vv
```

### Create
```
[user@linuxserver ~]$ pvcreate /dev/<Partition>
[user@linuxserver ~]$ vgcreate <VolGroup> /dev/<Partition>
[user@linuxserver ~]$ lvcreate -L 50G -n <VolName> <VolGroup>
Ahora puedes montar manualmente el volúmen o añadirlo en el fstab
```

### Extend
```
[user@linuxserver ~]$ vgextend <VolGroup> /dev/<Partition>
[user@linuxserver ~]$ vextend -l <options> /dev/mapper/<VolGroup>
[user@linuxserver ~]$ xfs_growfs /dev/mapper/<VolGroup>
options:
+100%FREE
+50G
```

### Delete
```
Antes de eliminar un volúmen montado debemos desmontarlo
[user@linuxserver ~]$ vremove /dev/mapper/<VolGroup>/<VolName>
```
![image](https://github.com/lluisrc/chuletarioBash/assets/60383607/4fdb81c4-b848-4701-b3c0-c7d30a22b8a6)

![[ChuletasLVM.drawio]]



![[RAC Oracle Prod (1).pdf]]