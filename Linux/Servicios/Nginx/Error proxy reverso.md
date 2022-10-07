Log error:
2021/11/07 17:58:19 [crit] 3012#0: *98 connect() to [::1]:8081 failed (13: Permission denied) while connecting to upstream, client: 192.168.1.43, server: 192.168.1.201, request: "GET / HTTP/1.1", upstream: "http://[::1]:8081/", host: "192.168.1.201"

Causa:
SELinux prevent connections on port 7990 for the nginx process

Buscamos por internet, comando:
semodule -i mynginx.pp

que es SELinux:
Security-Enhanced Linux es un módulo de seguridad para el kernel Linux, implementado utilizando el framework del núcleo Linux Security Modules, que proporciona el mecanismo para implementar una políticas de control de acceso de tipo Control de acceso obligatorio y control de acceso basado en roles​

que es audit2allow
La utilidad audit2allow recopila información de los registros de operaciones denegadas y luego genera las reglas de autorización de la política de SELinux. Después de analizar los mensajes de denegación según la Sección 10.10.3.7, “Mensajes de alerta”, y si no hay cambios de etiqueta o booleanos permitidos el acceso, use audit2allow para crear un módulo de política local. Cuando SELinux niega el acceso, la ejecución de audit2allow genera reglas de aplicación de tipos que permiten el acceso previamente denegado.

que es semodule -i mynginx
semodule is the tool used to manage SELinux policy modules, including installing, upgrading, listing and removing modules.