# Inventario ansible
El inventario es un archivo donde irán descritos todos los hosts remotos a gestionar.
Por defecto lo encontramos en la ruta `/etc/ansible/hosts`. 

También podemos crear nuestro archivo personalizado de inventario, se lo indicamos a ansible para que sepa donde ir a buscar (en caso de un comando ad hoc lo hacemos con `-i <nuestro_inventairo>`).

## Estructura del inventario
````
# Grupo de servidores
[servidores-web]
192.168.1.50
192.168.1.51
192.168.1.52
192.168.1.53
192.168.1.54

# Grupo de bases de datos
[servidores-db]
192.168.1.55
192.168.1.56
192.168.1.57

# Agrupar los dos grupos
[web-y-db:children]
servidores-web
servidores-db
````

Cuando ejecutamos un playbook o un comando ad hoc vamos a realizar tareas sobre hosts remostos definidos en el inventario que pueden ser:
- Todos --> `all`
- Un grupo --> `-l servidores-web`
- Uno --> `192.168.1.50`