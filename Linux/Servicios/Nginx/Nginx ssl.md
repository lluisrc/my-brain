Seguir los pasos en la página de cerbot:

(
Se ha instalado el certificado de lets encrype en nginx:
 Tener un dominio en propiedad.
 Tener un nginx corriendo en el puerto 80
 La configuración de nginx debe tener definido el nameserver con el dominio correspondiente.
 -- Creo que certbot hace una petición al dominio definido en -d y comprueba que la ip de destino es la misma de donde se ejecuta el comando y que es capaz de llegar al virtualhost

````
yum install epel-release
yum install snapd
systemctl enable --now snapd.socket
ln -s /var/lib/snapd/snap /snap
desacrivamos el selinux (sestatus --> para comprobar)
snap install core
snap refresh core
snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot
certbot --nginx -d <dominio> // certbot certonly --nginx -d <dominio>
# certbot renew --dry-run
````
)

He obtenido el certificado de cervbot sin que me edite el fichero de configuración de nginx 
/etc/letsencrypt/live/lluisrocacanellas.com/fullchain.pem
/etc/letsencrypt/live/lluisrocacanellas.com/privkey.pem

````
server {
        listen 443;

        ssl on;
        ssl_certificate /etc/letsencrypt/live/lluisrocacanellas.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/lluisrocacanellas.com/privkey.pem;

        root /var/www/html;
        server_name lluisrocacanellas.com www.lluisrocacanellas.com;
        location / {
            index index.nginx-debian.html;
        }
}

server {
        listen 80;
        root /var/www/html;
        server_name lluis.com www.lluis.com;
        location / {
            index test1.html;
        }
}
````