# docker-elasticsearch
Elasticsearch for Docker on Alpine

## Elasticsearch Master 5.6

- [rbekker87/elasticsearch:master-5.6-alpine](https://hub.docker.com/r/rbekker87/elasticsearch/tags/)

This image uses Elasticsearch version 5.6 on Alpine and has `discovery.zen.ping.unicast.hosts=es-master`, so in docker swarm mode if more services gets created, they will be able to resolve `es-master` dns address, and will be joined to the elasticsearch cluster.

## Elasticsearch Standalone 5.6

- [rbekker87/elasticsearch:5.6-alpine](https://hub.docker.com/r/rbekker87/elasticsearch/tags/)

This image uses Elasticsearch version 5.6 on Alpine and is for testing or delopment reasons, as the image was built without `discovery.zen.ping.unicast.hosts`.

## Elasticsearch Master 2.4

- [rbekker87/elasticsearch:master-2.4-alpine](https://hub.docker.com/r/rbekker87/elasticsearch/tags/)

This image uses Elasticsearch version 2.4.6 on Alpine and has `discovery.zen.ping.unicast.hosts=es-master`, so in docker swarm mode if more services gets created, they will be able to resolve `es-master` dns address, and will be joined to the elasticsearch cluster.

## Elasticsearch Standalone 2.4

- [rbekker87/elasticsearch:2.4-alpine](https://hub.docker.com/r/rbekker87/elasticsearch/tags/)

This image uses Elasticsearch version 2.4.6 on Alpine and is for testing or delopment reasons, as the image was built without `discovery.zen.ping.unicast.hosts`.

# Usage:

## Docker Swarm:

Create the overlay network:

```
$ docker network create --driver overlay esnet
```

Create the Master:

```
$ docker service create --name es-master --network esnet --publish 9200:9200 rbekker87/elasticsearch:master-5.6-alpine
```

Create 2 more nodes:

```
$ docker service create --name es-data-1 --network esnet rbekker87/elasticsearch:master-5.6-alpine
$ docker service create --name es-data-2 --network esnet rbekker87/elasticsearch:master-5.6-alpine
```

Query the Nodes API:

```
$ curl -XGET http://127.0.0.1:9200/_cat/nodes?v
ip       heap.percent ram.percent cpu load_1m load_5m load_15m node.role master name
10.0.7.6           27          88   7    0.75    0.64     0.40 mdi       -      be50f2065c07
10.0.7.2           30          88   7    0.75    0.64     0.40 mdi       *      aa77904e6a7e
10.0.7.4           28          88   7    0.75    0.64     0.40 mdi       -      0ce6a8ee26fe
```
