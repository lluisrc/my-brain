# Setup influxdb 1.8 en Ubuntu
---
Descargar e instalar el paquete
````terminal
$ wget https://dl.influxdata.com/influxdb/releases/influxdb-1.8.9.x86_64.rpm
$ yum localinstall telegraf-1.20.0-1.x86_64.rpm
````

Arrancar el servicio influxdb
````terminal
$ systemctl start influxdb
````

Comprobamos que el servicio está arrancado correctamente
````termianl
$ influxd
````

Nos conectamos a la shell de influx
````termianl
$ influx
````
---
## Comandos básicos en la shell de influx
Ver las bases de datos
````sql
> SHOW DATABASES
````

Crear una base de datos
````sql
> CREATE DATABASE <mydb>
````

Entrar en una base de datos
```sql
> USE mydb
```

Ver las tablas
```sql
> SHOW MEASUREMENTS
```

Insertar un registro
```sql
> INSERT <MEASUREMENT>,<key>=<value>,<key>=<value>,<key>=<value>
```

Ver las politicas de retención
```sql
> SHOW RETENTION POLICIES
```

Ver registros de las tablas
````sql
> SELECT * FROM <MEASUREMENT>
````