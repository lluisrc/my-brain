En la ruta --> /etc/nginx/conf.d/x.conf van a estar configurados todos los virtualhosts.
Los includes son punteros a la ruta que indican.
Mucha confiugración está por defecto, por ejemplo el archivo index.html el landing page.

Configuramos el archivo /etc/nginx/nginx.conf
Nos interesa el contenido del server:
server_name: nombre del virtualhost
root: es el path root del virtualhost
location: en cualquiera localización hará lo siguiente...

````
user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
        worker_connections 768;
        # multi_accept on;
}

http {
        # Basic Settings

        sendfile on;
        tcp_nopush on;
        tcp_nodelay on;
        keepalive_timeout 65;
        types_hash_max_size 2048;

        include /etc/nginx/mime.types;
        default_type application/octet-stream;



        # SSL Settings

        ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
        ssl_prefer_server_ciphers on;



        # Logging Settings

        access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;



        # Virtual Host Configs

        include /etc/nginx/conf.d/*.conf;
        include /etc/nginx/sites-enabled/*;

}
````

Este archivo de abajo es del include /etc/nginx/sites-enabled/* y está configurado como vhots
````
server {
        listen 80;
        root /var/www/html;
        server_name lluisrocacanellas.com www.lluisrocacanellas.com;
        location / {
            index index.nginx-debian.html;
        }
		error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
}

server {
        listen 80;
        root /var/www/html;
        server_name lluis.com www.lluis.com;
        location / {
            index test1.html;
        }
		error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
}
````