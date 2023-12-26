
```terminal
[linuxuser@linuxserver ~]$ sudo apt update
[linuxuser@linuxserver ~]$ sudo apt install mysql-server
```
Configuramos el nivel de complejidad de contraseña
Deshabilitamos acceso remoto del usuario root
No permitimos el acceso de usuarios anónimos
```
[linuxuser@linuxserver ~]$ sudo mysql_secure_installation
```
```sql
[linuxuser@linuxserver ~]$ sudo mysql -u root
sql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
sql> CREATE USER 'nombre_usuario'@'%' IDENTIFIED BY 'tu_contraseña';
sql> GRANT ALL PRIVILEGES ON *.* TO 'nombre_usuario'@'%';
sql> FLUSH PRIVILEGES;
sql> exit
```
```
[linuxuser@linuxserver ~]$ sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
bind-address = 0.0.0.0
mysqlx-bind-address = 0.0.0.0
```
```
[linuxuser@linuxserver ~]$ sudo systemctl restart mysql
```
Revisamos los logs en /var/log/mysql/error.log
```

[linuxuser@linuxserver ~]$ tail -f /var/log/mysql/error.log
```