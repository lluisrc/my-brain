Setup nginx en CentOS
---
Instalar Nginx
````terminal
# yum install nginx -y
# systemctl enable nginx
# systemctl start nginx
````
(Añadir .html en /usr/share/nginx/html)
````terminal
$ firewall-cmd --permanent --add-service=http
$ firewall-cmd --permanent --add-service=https
$ firewall-cmd --reload
````

Comprobamos, con un navegador, que llegamos a la landing page. localhost.com
