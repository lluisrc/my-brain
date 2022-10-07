/etc/nginx/nginx.conf:
````
server {
        server_name  lluisroca.com;
        listen 80;
        listen [::]:80;
        location / {
        proxy_pass http://127.0.0.1:8081/;
        }
    }
````
Cuando llega una petición la redirige a esta url

proxy_pass http://127.0.0.1:8081/;