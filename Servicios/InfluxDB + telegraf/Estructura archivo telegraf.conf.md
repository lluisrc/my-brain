# Estructura archivo telegraf.conf
El archivo telegraf.conf se encuentra en el siguiente path `/etc/telegraf/telegraf.conf`
### [global_tags]
Especifica una etiqueta en formato clave valor.
````
[global_tags]
dc = "us-east-1"
````

### [agent]
- **interval**: El intervalo de tiempo con los que saca los inputs
- **round_interval**: Redondea el intervalo, si el intervalo está en 10s, a tiempo de reloj se ejecuta a las 00:00, 00:10, 00:20
- **metric_batch_size**: El máximo de metricas que envía a la vez
- **metric_buffer_limit**: Número máximo de métricas que están en el buffer y por lo tanto no están escritas por el output.
- **collection_jitter**
- **flush_interval**
- **flush_jitter**
- **precision**
- **debug**
- **quiet**
- **logtarget**
- **logfile**
- **logfile_rotation_interval**: El intervalo de tiempo que tarda en rotar el logfile, si está en 0 no rota.
- **logfile_rotation_max_size**: El tamaño ocupa el archivo logfile para que rote
- **logfile_rotation_max_archives**: El máximo de rodatos que mentiene. Si está en -1 no elimina ninguno.
- **log_with_timezone**
- **hostname**
- **omit_hostname**

### [inputs.xxxx]
- **alias**: Nombre de la instancia del plugin
- **interval**: Sustituye el intervalo seteado en el _[agent]_
- **precision**
- **collection_jitter**
- **name_override**: Sobreesctibe el nombre de la tabla, por defecto es el nombre del plugin _xxxx_
- **name_prefix**: Especifica el prefijo del nombre de la tabla
- **name_suffix**: Especifica el sufijo del nombre de la tabla
- **tags**

````
[[inputs.cpu]]
  name_override = "foobar"
  percpu = false
  totalcpu = true
````

### [outputs.xxxx]
- **alias**: Nombre de la instancia del plugin
- **flush_interval**
- **flush_jitter**
- **metric_batch_size**: El máximo de metricas que envía a la vez, sustituye el valor seteado en el agente
- **name_override**: Sobreesctibe el nombre de la tabla, por defecto es el nombre del plugin _xxxx_
- **name_prefix**: Especifica el prefijo del nombre de la tabla
- **name_suffix**: Especifica el sufijo del nombre de la tabla

````
[[outputs.influxdb]]
  urls = [ "http://example.org:8086" ]
````

### [processors.xxxx]
¿?

### [aggregators.xxxx]
Producen nuevas métricas después de examinar las métricas durante un período de tiempo, como _promedio_, _máximo_ y _mínimo_
- **alias**: Nombre de la instancia del plugin
- **period**
- **delay**
- **grace**
- **drop_original**
- **name_override**: Sobreesctibe el nombre de la tabla, por defecto es el nombre del plugin _xxxx_
- **name_prefix**: Especifica el prefijo del nombre de la tabla
- **name_suffix**: Especifica el sufijo del nombre de la tabla
- **tags**

````
[[aggregators.minmax]]
  period = "30s"        # send & clear the aggregate every 30s.
  drop_original = true  # drop the original metrics.
````