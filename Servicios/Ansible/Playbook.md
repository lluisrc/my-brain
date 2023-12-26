# Playbook
Un playbook en un archivo .yaml que contiene un conjunto de plays que realizan ciertas tareas para definir un aprovisionamiento concreto para uno o varios hosts remotos.
## Estructura
Esta es la estructura de un playbook estandar
````
- name: Play1						# Nombre del play
  hosts: all						# Indica a que hosts del inventario va dirigido
  remote_user: lluis				# Con que usuario se va a conectar
  tasks:							# Aqui se listan las tareas del play
  - name: Execute command "date"	# Esto es el nombre de la terea
    command: date					# Esto es el módulo que utiliza + la acción que realiza (propia del módulo)

- name: Play2
  hosts: all
  remote_user: lluis
  tasks:
  - name: Install web service
    apt:
      name: apache2
      state: present
    become: yes
````
## Ejecución
````terminal
$ ansible-playbook <archivo.yaml>
````

## Become
El become de un playbook se define en una tarea, equivale a realizar la tarea con un sudo, de esta forma puede ejecutar las tareas con privilegios de administrador.
Esta va genial, por ejemplo, para gestionar servicios.
Para indicarle la contraseña del sudo, en el comando de ejecución del palybook como parámetro añadimos `-K`