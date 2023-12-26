1. Con el código más reciente de GitHub, el desarrollador realiza el desarrollo en local, atacando al mysql de staging. (Front debe atacar al Back en local)
```
[root@des-moviemapp backend_moviemapptv]# nodemon app.js
[root@des-moviemapp frontend_moviemapptv]# npm run dev
```
2. Una vez a terminado el desarrollo subimos el código a GitHub, si hemos modificado el front, este también lo subimos. El directorio `node_modules/` no deben subirse a GitHub
```
[root@des-moviemapp ~]# git add .
[root@des-moviemapp ~]# git commit -m "some comment"
[root@des-moviemapp ~]# git push
```
3. A continuación movemos los archivos que componen el backend al directorio raíz que usamos para la aplicación Node, instalamos las dependencias
```
[root@des-moviemapp backend_moviemapptv]# npm install
```
4. Reiniciamos el servicio moviemapp.services
```
[root@des-moviemapp ~]# systemctl restart moviemapp.services
```