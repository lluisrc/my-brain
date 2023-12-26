descargamos binario
configurar acceso no-localhost
sudo sysctl -w vm.max_map_count=262144
arrancar primera vez
crear token hosts
hacer lo mismo para el segundo hosts pero no arrancamos por primera vez y hacemos esto
importar token
ahora el segundo en nodo secundario y siembre que hagas bin/elasticsearch se lanzará como parte del cluster

para hacer un get
curl -u elastic:contraseña -k -X GET "https://localhost:9200/_cat/nodes?v=true"