Install a centos8 machine with an static IP and Internet access.


## Disabling SELinux
Edit /etc/selinux/config file, `SELINUX=disabled`
```
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of these three values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
```
Reboot the vm

## Installing mongodb
Create a `/etc/yum.repos.d/mongodb-org-6.0.repo` file so that you can install MongoDB directly using `yum`:

```
[mongodb-org-6.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/6.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-6.0.asc
```
To install the latest stable version of MongoDB, issue the following command:
```
yum install -y mongodb-org
systemctl start mongod
systemctl enable mongod
```
Si sale un error como este:
![[Pasted image 20230211120019.png]]

Debemos setear el type of CPU a host
![[Pasted image 20230211115757.png]]


## Crear usuario (mirar si se puede mejorar el procedimiento para best practices en privilegios mongodb)
```termianl
$ mongosh
test> show databases
test> use admin
admin> db.createUser({user: "dbroot",pwd: "dbroot",roles: [ { role: "root", db: "admin" } ]})

Ver usuarios:
use admin
show users
```

## En el archivo de .conf: sustituimos la ip 127.0.0.1 por 0.0.0.0 y añadimos autenticación

```termianl
$ vim /etc/mongod.conf
```

```
net:
  port: 27017
  bindIp: 0.0.0.0  # Enter 0.0.0.0,:: to bind to all IPv4 and IPv6 addresses or, alternatively, use the net.bindIpAll setting.
security:
  authorization: "enabled"
```

```termianl
$ systemctl restart mongod
```

## Habilitar puertos del firewalld

```termianl
$ systemctl status firewalld
$ firewall-cmd --permanent --add-port=27017/tcp
$ firewall-cmd --reload
$ firewall-cmd --list-ports
```
## Prueba conexión desde mongodb compass
![[Pasted image 20230211121714.png]]

## Install nodejs
```
[root@des-moviemapp /]# dnf install nodejs -y
[root@des-moviemapp /]# node -v
v10.23.1

# mkdir /src
# cd /src
# git clone https://github.com/lluisrc/moviemapp.tv.git
[root@des-moviemapp src]# cd moviemapp.tv/
[root@des-moviemapp moviemapp.tv]# npm install
[root@des-moviemapp moviemapp.tv]# node app.js
```
Si no s sale un error como el siguiente:
```
/src/moviemapp.tv/node_modules/whatwg-url/lib/encoding.js:2
const utf8Encoder = new TextEncoder();
                    ^
ReferenceError: TextEncoder is not defined
    at Object.<anonymous> (/src/moviemapp.tv/node_modules/whatwg-url/lib/encoding.js:2:21)
    at Module._compile (internal/modules/cjs/loader.js:778:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)
    at Module.require (internal/modules/cjs/loader.js:692:17)
    at require (internal/modules/cjs/helpers.js:25:18)
    at Object.<anonymous> (/src/moviemapp.tv/node_modules/whatwg-url/lib/url-state-machine.js:5:34)
    at Module._compile (internal/modules/cjs/loader.js:778:30)
```
Añadimos la siguiente línea al principio del archivo /src/moviemapp.tv/node_modules/whatwg-url/lib/encoding.js:
`const { TextEncoder, TextDecoder } = require("util");`

## Comprobamos que node arranca correctamente
Abrimos los puertos del firewalld
```
[root@des-moviemapp moviemapp.tv]# firewall-cmd --zone=public --permanent --add-port 3000/tcp
[root@des-moviemapp moviemapp.tv]# firewall-cmd --reload
[root@des-moviemapp moviemapp.tv]# firewall-cmd --list-ports
```
Abrimos un navegador web y accedemos a la siguiete url: `http://192.168.1.107:3000/`

![[Pasted image 20230211123517.png]]

## Creamos nodejs como servicio
```
[root@des-moviemapp moviemapp.tv]# cd /lib/systemd/system/
[root@des-moviemapp system]# vim moviemapp.service
```
```
[Unit]
Description=LTPS NodeJS Test Application
After=network-online.target

[Service]
Restart=on-failure
WorkingDirectory=/src/moviemapp.tv/
ExecStart=/usr/bin/node /src/moviemapp.tv/app.js

[Install]
WantedBy=multi-user.target
```
```
[root@des-moviemapp system]# systemctl daemon-reload
[root@des-moviemapp system]# systemctl start moviemapp
[root@des-moviemapp system]# systemctl status moviemapp
[root@des-moviemapp system]# systemctl enable moviemapp

```
## Quitar la base de datos prod y popular la de desarrollo.
Editamos el fichero app.js para añadir las credenciales de acceso correctas para mongo de desarrollo
```
const DBSERVER = "192.168.1.107";
// ip de la base de datos mongodb

const BDMONGO = "moviemapp_desarrollo";
// La base de datos de mongodb

const username = encodeURIComponent("dbroot");
const password = encodeURIComponent("dbroot");
// Conexión a mongodb

```
Creamos la base de datos de desarrollo con la colección `locations`
![[Pasted image 20230211125543.png]]

Creamos el resto de colecciones:
![[Pasted image 20230211125701.png]]

Populamos estas colecciones con los siguientes archivos json/csv
![[json_moviemapp_18-3-22 (3).json]]
![[comunidades_autonomas.csv]]
![[provincias.csv]]
![[municipios.csv]]
![[Pasted image 20230211130244.png]]

Restart moviemapp service and check again

## Meter nginx por delante + SSL
```
[root@des-moviemapp ~]# dnf install nginx
[root@des-moviemapp ~]# vim /etc/nginx/nginx.conf
(sustituimos "server" por este:)
server {
        server_name  des_moviemapp.tv;
        listen 80;
        listen [::]:80;
        location / {
        proxy_pass http://192.168.1.107:3000/;
        }
    }

[root@des-moviemapp ~]# systemctl start nginx
[root@des-moviemapp ~]# systemctl enable nginx
```
```
[root@des-moviemapp ~]# firewall-cmd --zone=public --permanent --add-port 80/tcp
[root@des-moviemapp ~]# firewall-cmd --reload
[root@des-moviemapp ~]# firewall-cmd --list-ports
(podemos quitar el de 3000)
Checkeamos la url por el puerto 80
**en producción tenemos que escuche el puerto 443 con SSL, mirar la docu "Nginx ssl"**
```