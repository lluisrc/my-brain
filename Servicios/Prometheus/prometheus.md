prometheus

1. Prometheus server es un binario que lo descargas y ya

`./prometheus`

Estos son los parámetros:
--config.file /etc/prometheus/prometheus.yml
--storage.tsdb.path /var/lib/prometheus/
--web.console.templates=/etc/prometheus/consoles
--web.console.libraries=/etc/prometheus/console_libraries

--storage.tsdb.retention.time 15d
--storage.tsdb.retention.size 0


2. Los exporters son binarios que lo descargas y ya
./node_exporter

Estos son los parámetros:
--web.listen-address="<IP>:<port>"


Los workers exponen las metricas en /metrics, el servidor lo va a buscar


	1082699776 B
	1057356 K
	1032.68 M
	1 G
	


./alertmanager --config.file=alertmanager.yml