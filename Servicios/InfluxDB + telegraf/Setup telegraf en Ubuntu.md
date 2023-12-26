# Setup telegraf en Ubuntu
---
Descargar e instalar telegraf
```terminal
$ wget https://dl.influxdata.com/telegraf/releases/telegraf_1.20.0-1_amd64.deb
$ dpkg -i telegraf_1.20.0-1_amd64.deb
```

Este es la ruta del archvo de configuración de telegraf `/etc/telegraf/telegraf.conf`.
Vamos a editar este archivo con la información de output e input que nos interese. Debe quedar algo parecido a esto:

````terminal
$ vim /etc/telegraf/telegraf.conf
````
````
[global_tags]
[agent]
  interval = "10s"
  round_interval = true
  metric_batch_size = 1000
  metric_buffer_limit = 10000
  collection_jitter = "0s"
  flush_interval = "10s"
  flush_jitter = "0s"
  precision = ""
  hostname = ""
  omit_hostname = false
[[outputs.influxdb]]
   urls = ["http://127.0.0.1:8086"]
[[inputs.cpu]]
  percpu = true
  totalcpu = true
  collect_cpu_time = false
  report_active = false
[[inputs.disk]]
  ignore_fs = ["tmpfs", "devtmpfs", "devfs", "iso9660", "overlay", "aufs", "squashfs"]
[[inputs.diskio]]
[[inputs.kernel]]
[[inputs.mem]]
[[inputs.processes]]
[[inputs.swap]]
[[inputs.system]]
````

Levantamos el servicio
````termianl
$ systemctl start telegraf
````
---
## Variables de estorno en la configuración
Podemos setear variables para el archivo de configuración. Estas variables se configuran en `/etc/default/telegraf` 

````terminal
$ vim /etc/default/telegraf
````

````
INFLUX_URL="http://localhost:8086"
````
En el archivo de configuración se vería algo así
````
[[outputs.influxdb]]
   urls = ["${INFLUX_URL}"]
````
