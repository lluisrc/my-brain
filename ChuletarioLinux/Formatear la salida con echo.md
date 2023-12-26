La salida la podemos imprimir con el comando echo
```
[root@serverlinux ~]# echo "Soy lroca"
```
### Parámetros
| Argument | Description |
|:--------:| ----------- |
| -e | Interpreta el carácter \\ como acción |
| -n | No hace un "intro" de después de imprimir |

### Formatos \
| Argument | Description |
|:--------:| ----------- |
| \b | Quita los espacios en blanco |
| \n | Salto de línea |
| \t | Tabulación |
| \v | Sangría a la derecha |
| \r | Vuelve el cursor al principio de la linea |
| \c | El prompt continúa |
| \a | Alerta de sonido ¿? |
| \e\[0;31m | Color Rojo |

```bash
#!/bin/bash

endColour="\e[0m"
redColour="\e[0;31m"
greenColour="\e[0;32m"
yellowColour="\e[0;33m"
blueColour="\e[0;34m"
purpleColour="\e[0;35m"
cianColour="\e[0;36m"
greyColour="\e[0;37m"

echo -e "${redColour}Rojo${endColour}"
echo -e "${greenColour}Verde${endColour}"
echo -e "${yellowColour}Amarillo${endColour}"
echo -e "${blueColour}Azul${endColour}"
echo -e "${purpleColour}Violeta${endColour}"
echo -e "${cianColour}Cian${endColour}"
echo -e "${greyColour}Gris${endColour}"
```
