1. Con el código más reciente de GitHub, el desarrollador realiza el desarrollo en local, atacando al backend de staging.
```
[root@des-moviemapp ~]# npm run dev
```
2. Una vez a terminado subimos el código a GitHub, los directorios `dist/` y `node_modules/` no deben subirse a GitHub
```
[root@des-moviemapp ~]# git add .
[root@des-moviemapp ~]# git commit -m "some comment"
[root@des-moviemapp ~]# git push
```
3. A continuación hacemos un build para obtener los archivos estáticos
```
[root@des-moviemapp ~]# npm run build
```
4. Se generará un directorio llamado `dist/` copiamos el contenido de este direcotrio y lo pasamos al directorio raíz de la aplicación en Nginx, en este caso `/usr/shared/nginx/<app>/`