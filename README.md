Deployment snax node with elasticsearch backend and elasticsearch history api using docker

## Requirements:
* [Docker](https://www.docker.com) > 18
* [docker-compose](https://docs.docker.com/compose/install/) >= 3.7
* `vm.max_map_count=262144` in /etc/sysctl.conf
* 32Gb RAM

## Run:

```
mkdir elasticsearch
chmod g+rwx elasticsearch
chgrp 1000 elasticsearch
docker-compose up -d elasticsearch
git clone https://github.com/SnaxFoundation/es-history-api.git
cd es-history-api
bash ./index-templates.sh --action create --dir ./templates --url http://localhost:9200
cd ..
docker-compose up -d
