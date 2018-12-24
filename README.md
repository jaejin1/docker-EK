## Requirements

1. Install Docker version 17.05+
2. Install Docker Compose version 1.6.0+
3. Clone this repository

## Usage

### Build Dockerfile

* elasticsearch

```
$ cd docker/elasticsearch
$ docker build --build-arg ELK_VERSION=6.5.4 --build-arg SG_VERSION=24.0 -t {docker image name}:{tag} .
```

* kibana

```
$ cd docker/kibana
$ docker build --build-arg ELK_VERSION=6.5.4 --build-arg SG_VERSION_KIBANA=17 -t {docker image name}:{tag} .
```

### Change docker image name and tag in .env file

```
ELASTICSEARCH={elasticsearch docker image name}
KIBANA={kibana docker image name}
TAG={tag name}
```

### Run docker-compose

```
$ docker-compose up -d
```

Search Guard must be initialized after Elasticsearch is started:

```
$ docker-compose exec -T elasticsearch bin/init_sg.sh
```

## Check connection

#### Elasticsearch

* http://localhost:19200/

    * http://localhost:19200/_searchguard/authinfo

#### Kibana

* http://localhost:5601

