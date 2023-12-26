# Setup mongodb en CentOS
---
## Creamos un archivo con los parámetros del repositorio remoto de mongodb para yum

```` terminal
$ vim /etc/yum.repos.d/mongodb-org-5.0.repo
````
> [mongodb-org-5.0]
> name=MongoDB Repository
> baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/5.0/x86_64/
> gpgcheck=1
> enabled=1
> gpgkey=https://www.mongodb.org/static/pgp/server-5.0.asc
````termianl
$ yum install -y mongodb-org
$ systemctl start mongod
$ systemctl enable mongod
````
## Crear usuario root
````termianl
$ mongosh
test> show databases
test> use admin
admin> db.createUser({user: "dbroot",pwd: "dbroot",roles: [ { role: "root", db: "admin" } ]})
````
## En el archivo de .conf: sustituimos la ip 127.0.0.1 por 0.0.0.0 y añadimos autenticación
````termianl
$ vim /etc/mongod.conf
````
```
net:
  port: 27017
  bindIp: 0.0.0.0  # Enter 0.0.0.0,:: to bind to all IPv4 and IPv6 addresses or, alternatively, use the net.bindIpAll setting.
security:
  authorization: "enabled"
```
````termianl
$ systemctl restart mongod
````
## Habilitar puertos del firewalld
````termianl
$ systemctl status firewalld
$ firewall-cmd --permanent --add-port=27017/tcp
$ firewall-cmd --reload
$ firewall-cmd --list-ports
````


```
Autenticar como usuario:
db.auth("masteradmin", "l4m4m4d3r4")

Crear usuario:
db.createUser({user: "dbroot",pwd: "dbroot",roles: [ { role: "root", db: "admin" } ]})

Ver usuarios:
use admin
show users

Eliminar usuarios:
db.dropUser('dbroot')
```