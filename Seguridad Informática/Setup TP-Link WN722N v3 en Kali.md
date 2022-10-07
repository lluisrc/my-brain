TPlink WN722N v3 es una antena wifi.

Cuando conectamos esta antena en un linux, este linux utiliza el driver "8188eu" para hacerla funcionar. 8188eu no soporta el modo monitor.
En su defecto, debemos instalar un nuevo driver ("rtl8188eus") que nos permita poner la antena en modo monitor y real inyecciones.

##### Instalación

Como root:
````
[root@kalilinux ~ ]# apt update
[root@kalilinux ~ ]# apt upgrade
[root@kalilinux ~ ]# apt dist-upgrade
[root@kalilinux ~ ]# reboot
[root@kalilinux ~ ]# apt install linux-headers-$(uname -r)
[root@kalilinux ~ ]# apt install bc
[root@kalilinux ~ ]# apt install build-essential
[root@kalilinux ~ ]# apt install libelf-dev
[root@kalilinux ~ ]# apt install dkms
[root@kalilinux ~ ]# rmmod r8188eu.ko
[root@kalilinux ~ ]# git clone https://github.com/drygdryg/rtl8188eus
[root@kalilinux ~ ]# cd rtl8188eus
[root@kalilinux ~ ]# echo 'blacklist r8188eu'|sudo tee -a '/etc/modprobe.d/realtek.conf'
[root@kalilinux ~ ]# reboot
[root@kalilinux ~ ]# cd rtl8188eus
[root@kalilinux ~ ]# make && make install
[root@kalilinux ~ ]# reboot
````