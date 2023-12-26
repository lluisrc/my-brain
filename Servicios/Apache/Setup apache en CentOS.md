# Setup apache en CentOS
---
````terminal
$ yum install httpd -y
$ systemctl enable httpd
$ systemctl start httpd
````
(Añadir .html en /var/www/html/)
````terminal
$ firewall-cmd --permanent --add-service=http
$ firewall-cmd --permanent --add-service=https
$ firewall-cmd --permanent --reload
````