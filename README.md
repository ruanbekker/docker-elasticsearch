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
