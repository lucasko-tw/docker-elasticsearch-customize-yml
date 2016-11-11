## Dockerfile for Elasticsearch 2.3 with customize elasticsearch.yml
This is a example for runing elasticsearch 2.3 container and dynamic import customize elasticsearch.yml


### elasticsearch.yml

```yml
network.host: 0.0.0.0
cluster.name: "lucasko"
node.name: "ko-node-1"
node.master: true
node.data: true
discovery.zen.ping.multicast.enabled: false 

path.data: /data/data
path.logs: /data/logs
```

### Build image

```sh
	docker build -t es:1.0 . 
```

### Run container

```sh
	docker run -p 9200:9200 -p 9300:9300 --user elsearch  -v $PWD/data:/data -v $PWD/config:/elasticsearch/config  es:1.0 /elasticsearch/bin/elasticsearch 
```

### Check _plugin/head

	http://localhost:9200/_plugin/head/

