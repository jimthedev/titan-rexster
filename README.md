# titan-rexster

Titan v 0.5.4 w/Cassandra and ElasticSearch

This image improves upon by the (apobbati/titan-rexter image)[https://registry.hub.docker.com/u/apobbati/titan-rexster/] by implementing the following:

* Enable Rexter/Thrift/RPC in Cassandra by default, enabling Rexter to actually work.
* Adds a docker-compose yaml config

## Run using docker-compose

1. (Install docker-compose)[https://docs.docker.com/compose/install/].
2. Clone this repo and cd to the directory
3. Run `docker-compose up`
4. Run `boot2docker ip` to get the ip address of your docker VM.
5. Go to http://<IP-OF-VM>:8182 in your browser and you should see the Rexter page.

To use this image, you can use 

## Run manually using only docker

Run the dependencies:

```bash
docker run -d --name es1 elasticsearch
docker run -d --name cs1 jimthedev/cassandra
```

To run in development mode (showing logs in console):

```bash
docker build -t <NAME>/titan-rexster .
docker run -it -P --rm --name titan-rexster --link es1:elasticsearch --link cs1 <NAME>/titan-rexster
```

To run in production mode (as a daemon):

```bash
docker run -d -P --rm --name titan-rexster --link es1:elasticsearch --link cs1 <NAME>/titan-rexster
```

To see the server in action:
1. Run `boot2docker ip` to get the ip address of your docker VM.
2. Go to http://<IP-OF-VM>:8182 in your browser and you should see the Rexter page.