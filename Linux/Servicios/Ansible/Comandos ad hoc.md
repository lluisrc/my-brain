# Comandos ad hoc
Un comando ad hoc es una una tarea que se ejecuta en un momento dado, con unos parametros especificos para obtener un resultado concreto. Es lo que comunmente se conoce como "Ejecutar un comando en la termianl y que devuelva resultado."

---

## Parámetros
- -i definir el inventario (si se usa el inventario por defecto no hace falta definir)
- -l definir el all/grupo/host
- -u definir usuario a conectar
- -K pedir contraseña (no hace falta esto si tenemos la clave ssh configurada: [[Conigurar clave ssh en equipo remoto]])
- -m definir módulo
- -a definir argumento

````termianl
$ ansible all -u ansible -m ping
````

````termianl
$ ansible -l grupo1 -u lluis -a whoami
````