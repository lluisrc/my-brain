Instalamos Nginx
```
[root@des-moviemapp ~]# yum install nginx
```
Creamos el directorio donde se alojará nuestros archivos estáticos de react
```
[root@des-moviemapp ~]# mkdir /usr/shared/nginx/<directorio>
```
Creamos un archivio de configuración para crear un nuevo virtual host
```
[root@des-moviemapp ~]# vim /etc/nginx/conf.d/<archivo>.conf
```
Dentro de este archivo tendrá el siguiente contenido:
```
server {
    listen 81;
    listen [::]:81;

    root /usr/share/nginx/testlroca;
    index index.html;
}
```
Comprobamos la sintaxis de los archivos de configuración
```
[root@des-moviemapp ~]# nginx -t
```
Deshabilitamos el firewalld
```
[root@des-moviemapp ~]# systemctl stop firewalld
[root@des-moviemapp ~]# systemctl disable firewalld
```
Comprobamos entrando en la siguiente URL:
`http://<ip_nginx>:81/`

Para añadir SSL mirar más adelante como hacerto pero creo que necesito que el certbot me genere las claves pub y priv y añadir la siguiente configuración al virtualhost despues de listen 81
```
listen 443 ssl;
ssl_certificate /etc/letsencrypt/live/ejemplo.com/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/ejemplo.com/privkey.pem;
ssl_protocols TLSv1.2 TLSv1.3;
ssl_ciphers ECDHE-RSA-AES256-GCM-SHA512:DHE-RSA-AES256-GCM-SHA512:ECDHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-SHA384;
ssl_prefer_server_ciphers on;
ssl_session_cache shared:SSL:10m;
ssl_session_timeout 5m;
```