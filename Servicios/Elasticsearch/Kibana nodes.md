curl -O https://artifacts.elastic.co/downloads/kibana/kibana-8.11.3-darwin-x86_64.tar.gz
curl https://artifacts.elastic.co/downloads/kibana/kibana-8.11.3-darwin-x86_64.tar.gz.sha512 | shasum -a 512 -c - 
tar -xzf kibana-8.11.3-darwin-x86_64.tar.gz
mv kibana-8.11.3 kibana
cd kibana
configurar acceso no-localhost
bin/kibana
crear token kibana en elastic
entrar en la web para poner el token