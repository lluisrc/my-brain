# Ejecutar un comando al arranque del sistema
Editamos el archivo de crontab `crontab -e` y escribimosla siguinte instrucción
```
@reboot <instrucción>

Ejemplo:
@reboot /usr/bin/docker-compose -f /opt/docker/registros-canpedro/main/docker-compose.yml up -d
```