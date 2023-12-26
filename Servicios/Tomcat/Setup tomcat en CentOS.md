Descargamos e instalamos java (si no lo tenemos)
````termianl
$ wget https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.rpm
````

````termianl
$ yum localinstall <paquete>.rpm
````

Comprobamos
````termianl
$ java -version
````

Descargamos el binario tomcat
````termianl
$ wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.0.12/bin/apache-tomcat-10.0.12.tar.gz
````

Asignamos las variables de entorno
````terminal
$ export JAVA_HOME=<path_java> (/usr/java/jdk-17.0.1)
````

````terminal
$ export CATALINA_HOME=<path_java> (/root/apache-tomcat-10.0.12)
````

Arrancamos el servicio
````termianl
$ $CATALINA_HOME/bin/catalina.sh start
````

Cuidado con el firewall, hay que dar acceso a través del puerto 8080 (o deshabilitar el fw)
Comprobamos accediento con un navegador a la url localhost:8080

Para saber que puertos esta usando catalina lo miramos con `grep port $CATALINA_HOME/conf/server.xml`
https://help.clouding.io/hc/es/articles/360010691359-C%C3%B3mo-Instalar-Tomcat-con-Nginx-como-Reverse-Proxy-en-Ubuntu-18-04
