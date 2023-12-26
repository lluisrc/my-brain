Editamos el archivo de crontab `crontab -e` y escribimosla siguinte instrucción
```vim
@reboot <instrucción>

Ejemplo:
@reboot /usr/bin/docker-compose -f /opt/docker/registros-canpedro/main/docker-compose.yml up -d
```