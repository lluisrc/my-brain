Setup
Descargar los paquetes necesarios de los prerrequisitos (seguir la documentación oficial)
Añadir repositorio
Instalar desde el repositorio


apt update && apt -y install ca-certificates wget net-tools gnupg

wget https://as-repository.openvpn.net/as-repo-public.asc -qO /etc/apt/trusted.gpg.d/as-repository.asc

echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/as-repository.asc] http://as-repository.openvpn.net/as/debian jammy main">/etc/apt/sources.list.d/openvpn-as-repo.list

apt update && apt -y install openvpn-as



Llegados a este punto automáricamente hará el wizard y aparecerá la contraseña en pantalla

Para volver a ver la contraseña por  pantalla hay que consultar el archivo /usr/local/openvpn_as/init.log

2 tipos de accesos:
a) Entrar con el usuario administrador para gestionar el servicio de VPN
b) Entrar como usuario nominal para obtener el archivo de conexión a la VPN

Administrar servicio openvpn-as
/usr/local/openvpn_as/scripts/sacli stop
/usr/local/openvpn_as/scripts/sacli start
/usr/local/openvpn_as/scripts/sacli status
/usr/local/openvpn_as/scripts/sacli VPNSummary
/usr/local/openvpn_as/scripts/sacli VPNStatus


Funciona pero con ipv6 no va bien, los datos moviles utiliza ipv6 y no puede ser conectado por OpenVPN...

Mirar esto mas adelante
