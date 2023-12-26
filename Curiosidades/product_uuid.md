Este archivo muestra un identificador único que está asociado al hardware

Cuando hacemos un import de una vm se genera un nuevo product_uuid. A pesar que el disco sea el mismo el resto de hardware (CPU, mem, motherboard...) no son el mismo (new vm)

Para ver el product_uuid lanzamos el siguiente comando:
```
# cat /sys/class/dmi/id/product_uuid
```
