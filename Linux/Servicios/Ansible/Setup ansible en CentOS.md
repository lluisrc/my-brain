# Setup ansible en CentOS
---
Instalamos el repositorio EPEL e instalamos ansible
````terminal
$ yum install epel-release -y
$ yum install ansible -y
````

El archivo de configuración se encuentra en la siguiente rutra: `/etc/ansible/ansible.cfg`
El inventario se encuentra en la siguiente ruta: `/etc/ansible/hosts`

> _Nota: Ansible necesita que tanto el host central como los clientes tengan python instalado (ya viene por defecto)._

---
## Configuración ssh
Ansible ejecuta con el usuario actual instruciones que se ejecutan en sus clientes remotos a través del protocolo ssh.
Como configurar la clave ssh en los clientes remotos para que no pida contraseña cuando accedemos, está explicado en [[Conigurar clave ssh en equipo remoto]]
