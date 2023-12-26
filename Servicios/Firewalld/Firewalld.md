# Firewalld
Firewalld es un servicio de linux que proporciona un firewall a nivel de aplicación.

Comandos básicos:
````
[root@linuxlocal ~ ]# firewall-cmd --new-zone=000-allow --permanent  
[root@linuxlocal ~ ]# firewall-cmd --add-source 192.168.250.216 --zone=000-allow --permanent  
[root@linuxlocal ~ ]# firewall-cmd --add-source [192.168.0.0/16](http://192.168.0.0/16) --zone=block --permanent  
[root@linuxlocal ~ ]# firewall-cmd --add-service ssh --zone=000-allow --permanent  
[root@linuxlocal ~ ]# firewall-cmd --permanent --zone=public --set-target=DROP  
[root@linuxlocal ~ ]# firewall-cmd --permanent --zone=000-allow --change-interface=ens192  
[root@linuxlocal ~ ]# firewall-cmd --permanent --zone=block --change-interface=ens192
[root@linuxlocal ~ ]# firewall-cmd --reload


[root@linuxlocal ~ ]# firewall-cmd --permanent --zone=public --set-target=default  
[root@linuxlocal ~ ]# firewall-cmd --permanent --zone=block --remove-interface="ens192"  
[root@linuxlocal ~ ]# firewall-cmd --permanent --delete-zone=000-allow  
[root@linuxlocal ~ ]# firewall-cmd --reload
´´´´