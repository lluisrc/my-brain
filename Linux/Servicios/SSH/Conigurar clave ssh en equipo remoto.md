# Conigurar clave ssh en equipo remoto
---
En este ejemplo tenemos 2 nodos.
Nodo1 --> Servidor origen (local)
Noso2 --> Servidor destino (remoto)

El objetivo es generar una clave ssh de un usuario del nodo1 y esta clave la pasamos a un usuario del nodo2. De esta forma, cuando el usuario del nodo1 se conecte al usuario del nodo2 lo pueda hacer sin credenciales.

Generamos una clave ssh del usuario en el nodo1
````termianl
$ ssh-keygen
````

> Nota: En caso de que ya tengamos claves ssh para este usuario, las reemplazará por las nuevas.

Vemos que se han generado 2 archivos en la ruta `~/.ssh/`:
- *id_rsa*: Es la clave privada.
- *id_rsa.pub*: Es la clave pública

El contenido del archivo de la clave publica es algo parecido a esto. Esta clave contiene la clave ssh + el usuario + el host (El host es localhost, hay que cambiarlo por la ip correspondiente)
````
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDMiDYv5hf4A9ZJa8dQfu7kaBG0PFtJ67GnMnFjvxgw9qEh+f5CGPtihgYLADE8jcScthm04me3ps4ZDIgPZwykSkt73LT6xqKIv8phaGTJiuvR871xzw07XDuEQfr4uvtU0keHlDBP/ln9qkpmdgxbxsh7It/j+m8/zmPQCvEVxxxxxxxxxqAinNz/lXXS4ZMzQnMwSpcKbZPxxxxxxxxxxxxxx3M+2NG/HriE3rsU/MVYKiQgzS5jb4ZPgVGrwHQgkc/w/Yq6Ntx9IxxxxxoMVqmsn2pRkpDS5+cyb5vkDcjP53A1qgcNsn7X2f9YAo3GruCTGZUpys9sewSu2eiX1CdYHIEOtU2lXeilXXNSgjm5CRcTKqPdLgqNS4zIRMj2ONJFqaMemCPjxK6e9/8JmovqWh3+bEIFy8KzjNDZZlqi1SRFL2AIlxxxxxdI+VJ6sLlHRHZX9tzPfx+kbg/zR6zjF7/hzrJ2rSAS8vtgk8quV8= root@localhost.localdomain
````

Esta clave publica es la vamos a pasar a un usuario del nodo2 en la ruta `~/.ssh/authorized_keys`. Para ello lo podemos hacer de diferentes formas:
1. Automática
````termianl
$ ssh-copy-id <usuario_nodo2>@<nodo2>
````

2. Manual
Copiamos y la pegamos la clave publica generada y la pegamos en la ruta `~/.ssh/authorized_keys` del nodo2.

> Nota: Si no existen estos directorios/archivos los creamos `mkdir .ssh` y `vim authorized_keys`



aqui

jfgas