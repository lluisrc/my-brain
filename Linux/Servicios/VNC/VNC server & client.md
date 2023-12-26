# TigerVNC-server
Como root:
1. Instalar paquete `dnf install tigervnc-server`
2. Copiar el servicio de la ruta de libreria a la ruta de servicio `cp /lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@.service`
3. Crear usuario en el archivo `/etc/tigervnc/nvcserver.users` (El usuario debe existir en el sistema)
4. Entramos como un usuario para setear la contraseña vnc `su - <usuario>` y después `vncpasswd`
5. Arrancamos el servicio indicando el usuario de conexión `systemctl start vncserver@:4.service` (El ":4" representa el id que indicamos en le archivo de manejo de usuarios)

# VNC Viewer
Para realizar la conexión con el cliente VNC Viewer debemos saber que vnc trabaja en el puerto 5900. También hay que tener en cuenta que cada conexión (la conexión que definimos anteriormente) irá por un puerto diferente. Es decir, la conexión :4 irá por el puerto 5904

Nos tendremos que conectar a la <ip>:5904, el usuario ya está definido en la conexión. SOlo escribiremos la vncpasswd y pa dentro!!