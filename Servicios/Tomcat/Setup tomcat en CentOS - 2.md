  
![](https://tutorialesit.com/wp-content/uploads/2020/02/Linux_Tomcat_9_CentOS_8_1.jpg)

# Linux: Como instalar Tomcat 9 en CentOS 8

12/03/2020 por [Sergio Portillo](https://tutorialesit.com/author/admin/ "Ver todas las entradas de Sergio Portillo")

En esta entrada voy a explicaros paso a paso como podéis instalar Tomcat 9 en CentOS 8.

Para aquellos que no lo conozcáis Apache Tomcat es un contenedor open-source de java Servlet, JavaServer Pages, Java Expression Language y Java WebSocket.

## **Prerequisitos**

-   Usuario con privilegios sudo para poder realizar la instalación de los distintos paquetes.
-   Disponer de una conexión a Internet para poder descargar Apache Tomcat.

## **Instalación OpenJDK**

Tomcat 9 requiere Jave SE 8 o superior. Para este ejemplo instalaremos OpenJDK, la implementación open-source de Java que incorpora por defecto Java development y el runtime.

Para realizar la instalación simplemente tendremos que ejecutar el siguiente comando:
````
[user@linuxserver ~]$ sudo dnf install java-11-openjdk-devel
````
## **Creación usuario para Tomcat**

No es una buena práctica de seguridad ejecutar Tomcat con el usuario root es por ello que vamos a crear un usuario específico para este fin.

El usuario se llamará tomcat y su directorio home estará ubicado en la ruta /opt/tomcat. Este usuario será el encargado de iniciar el servicio de Tomcat.
````
[user@linuxserver ~]$ sudo useradd -m -U -d /opt/tomcat -s /bin/false tomcat
````
## **Descarga de Tomcat**

Vamos a descargar la última versión disponible de Tomcat 9.0.x desde la [web oficial del proveedor](https://tomcat.apache.org/download-90.cgi).

**Nota:** En el momento en el que estoy escribiendo esta entrada la última versión disponible es la 9.0.31 por lo que es recomendable que os vayáis a la página oficial de Tomcat para ver si hay alguna nueva versión disponible.

Nos descargaremos el fichero de instalación en la carpeta /tmp
````
[user@linuxserver ~]$ cd /tmp
[user@linuxserver ~]$ wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.31/bin/apache-tomcat-9.0.31.tar.gz
````
Descomprimimos el fichero.
````
[user@linuxserver ~]$ tar -xf apache-tomcat-9.0.31.tar.gz
````
Movemos los ficheros descomprimidos a la carpeta que creamos anteriormente en la ruta /opt/tomcat.
````
[user@linuxserver ~]$ sudo mv apache-tomcat-9.0.31 /opt/tomcat/
````
Cambiamos los permisos de la carpeta /opt/tomcat y todas sus subcarpetas para que el propietario pase a ser el usuario tomcat.
````
[user@linuxserver ~]$ sudo chown -R tomcat: /opt/tomcat/
````
Convertimos los scripts, que podemos encontrar dentro del subdirectorio bin, en ficheros ejecutables.
````
[user@linuxserver ~]$ sudo sh -c 'chmod +x /opt/tomcat/apache-tomcat-9.0.31/bin/*.sh'
````
## **Creación servicio Tomcat**

Para poder ejecutar Tomcat como un servicio tendremos que crear un fichero que llamaremos tomcat.service el cual ubicaremos en la ruta /etc/systemd/system
````
[user@linuxserver ~]$ sudo nano /etc/systemd/system/tomcat.service
````
Copiamos lo siguiente en el fichero:

**Nota:** En el caso que os hayáis descargado una versión distinta a la que utilizo en este ejemplo deberéis cambiar las rutas por las que useis.
````
[Unit]
Description=Tomcat 9 servlet container
After=network.target

[Service]
Type=forking

User=tomcat
Group=tomcat

Environment="JAVA_HOME=/usr/lib/jvm/jre"
Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"

Environment="CATALINA_BASE=/opt/tomcat/apache-tomcat-9.0.31"
Environment="CATALINA_HOME=/opt/tomcat/apache-tomcat-9.0.31"
Environment="CATALINA_PID=/opt/tomcat/apache-tomcat-9.0.31/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"

ExecStart=/opt/tomcat/apache-tomcat-9.0.31/bin/startup.sh
ExecStop=/opt/tomcat/apache-tomcat-9.0.31/bin/shutdown.sh

[Install]
WantedBy=multi-user.target
````
Guardamos los cambios y cerramos el editor.

Informamos al sistema de la creación de un nuevo servicio, para ello ejecutaremos el siguiente comando:
````
[user@linuxserver ~]$ sudo systemctl daemon-reload
````
Configuramos el servicio Tomcat para que se inicie automáticamente al arranque del servidor y a continuación lo iniciamos manualmente.
````
[user@linuxserver ~]$ sudo systemctl enable tomcat
[user@linuxserver ~]$ sudo systemctl start tomcat
````
Comprobamos que el servicio se ha iniciado correctamente. Para ello ejecutaremos el siguiente comando y comprobaremos que el servicio se encuentra en el estado active (running).
````
[user@linuxserver ~]$ sudo systemctl status tomcat

tomcat.service - Tomcat 9 servlet container
Loaded: loaded (/etc/systemd/system/tomcat.service; enabled; vendor preset: disabled)
Active: active (running) since Tue 2020-02-25 15:39:37 CET; 29min ago
Process: 15290 ExecStop=/opt/tomcat/apache-tomcat-9.0.31/bin/shutdown.sh (code=exited, status=0/SUCCESS)
Process: 15323 ExecStart=/opt/tomcat/apache-tomcat-9.0.31/bin/startup.sh (code=exited, status=0/SUCCESS)
Main PID: 15331 (java)
Tasks: 33 (limit: 26213)
Memory: 212.7M
CGroup: /system.slice/tomcat.service
      └─15331 /usr/lib/jvm/jre/bin/java -Djava.util.logging.config.file=/opt/tomcat/apache-tomcat-9.0.31/conf/logging.properties -Djava.util.log
````
**Nota:** En el caso que no arranque el servicio por temas de permisos y después de haberle aplicado los permisos de ejecución tal y como indiqué anteriormente es posible que tengas que considerar deshabilitar SELinux.
````
setenforce 0
````
## **Configuración Firewall**

Para acceder a la interfaz web de configuración de tomcat desde fuera del propio servidor tendremos que abrir el puerto 8080 en el Firewall de Linux. Utilizaremos los siguientes comandos:
````
[user@linuxserver ~]$ sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent 
[user@linuxserver ~]$ sudo firewall-cmd --reload
````
## **Configuración de la Web de Administración de Tomcat**

Para poder acceder a la consola de administración de Tomcat vía web tendremos que crear en primer lugar un usuario.

Los usuarios y los roles son definidos en el fichero tomcat-user.xml

Abriremos el fichero:
````
[user@linuxserver ~]$ sudo nano /opt/tomcat/apache-tomcat-9.0.31/conf/tomcat-users.xml
````
Para añadir un usuario agregaremos en el fichero lo siguiente:
````
<tomcat-users>
   <role rolename="admin-gui"/>
   <role rolename="manager-gui"/>
   <user username="admin" password="contraseña que deseemos" roles="admin-gui,manager-gui"/>
</tomcat-users>
````
Por defecto la web de administración de Tomcat está configurada para permitir el acceso sólo desde el propio localhost. Si queremos acceder desde por ejemplo otro PC tendremos que realizar las siguientes modificaciones en los 2 ficheros que os indico a continuación.
````
[user@linuxserver ~]$ sudo nano /opt/tomcat/apache-tomcat-9.0.31/webapps/manager/META-INF/context.xml
````
Comentamos la siguiente porción de texto.
````
<Context antiResourceLocking="false" privileged="true" >
<!--
  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->
</Context>
````

````
sudo nano /opt/tomcat/apache-tomcat-9.0.31/webapps/host-manager/META-INF/context.xml
````
Comentamos la siguiente porción de texto.
````
<Context antiResourceLocking="false" privileged="true" >
<!--
  <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
-->
</Context>
````
Reiniciamos el servicio de Tomcat para aplicar los últimos cambios que hemos realizado.
````
[user@linuxserver ~]$ sudo systemctl restart tomcat
````
Y listo ya podremos abrir desde cualquier navegador la dirección http://<dominio o dirección IP>:8080 y nos deberá aparecer una pantalla similar a la siguiente:

![](https://tutorialesit.com/wp-content/uploads/2020/02/Linux_Tomcat_9_CentOS_8_1.jpg)

Espero os haya servido de utilidad

Fuente de información
https://tutorialesit.com/linux-como-instalar-tomcat-9-en-centos-8/