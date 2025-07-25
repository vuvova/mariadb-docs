# MariaDB Container Cheat Sheet

## Get the images

Images can be found on [MariaDB Docker Hub](https://hub.docker.com/_/mariadb).\
To get the list of images run

```
$ docker images -a
```

## Create the network

```
$ docker network create mynetwork
```

It is good practice to create the container network and attach the container to the network.

`Start the container with server options`

To start the container in the background with the MariaDB server image run:

```
$ docker run --rm --detach \
--env MARIADB_ROOT_PASSWORD=sosecret \
--network mynetwork \
--name mariadb-server \
mariadb:latest
```

Additionally [|environment variables](mariadb-server-docker-official-image-environment-variables.md) are also provided.

## Get the list of running containers

```
$ docker ps
CONTAINER ID   IMAGE            COMMAND                  CREATED          STATUS          PORTS      NAMES
ad374ec8a272   mariadb:latest   "docker-entrypoint.s…"   3 seconds ago    Up 1 second     3306/tcp   mariadb-server
```

Note: specify the flag **-a** in case you want to see all containers

## Start the client from the container

To start the _mariadb_ client inside the created container and run specific commands, run the following:

```
$ docker exec -it mariadb-server mariadb -psosecret -e "SHOW PLUGINS"
```

## Inspect logs of a container

```
$ docker logs mariadb-server
```

In the logs you can find status information about the server, plugins, generated passwords, errors and so on.

## Restart the container

```
$ docker restart mariadb-server
```

## Run commands within the container

```
$ docker exec -it mariadb-server bash
```

## Use a volume to specify configuration options

```
$ docker run --detach --env MARIADB_USER=anel \
  --env MARIADB_PASSWORD=anel \
  --env MARIADB_DATABASE=my_db \
  --env MARIADB_RANDOM_ROOT_PASSWORD=1 \
  --volume $PWD/my_container_config:/etc/mysql/conf.d:z \
  --network mynetwork \
  --name mariadb-server1 \
   mariadb:latest
```

One can specify custom [configuration files](../../../../configuring-mariadb/configuring-mariadb-with-option-files.md) through the **/etc/mysql/conf.d** volume during container startup.

## Use a volume to specify grants during container start

```
$ docker run --detach --env MARIADB_USER=anel\
  --env MARIADB_PASSWORD=anel \
  --env MARIADB_DATABASE=my_db \
  --env MARIADB_RANDOM_ROOT_PASSWORD=1 \
  --volume $PWD/my_init_db:/docker-entrypoint-initdb.d \
  --network mynetwork \
  --name mariadb-server1 \
   mariadb:latest
```

User created with the environment variables has full grants only to the _MARIADB\_DATABASE_. In order to override those grants, one can specify grants to a user, or execute any SQL statements from host file to **docker-entrypoint-initdb.d**. In the _local\_init\_dir_ directory we can find the file, created like this:

```
$ echo "GRANT ALL PRIVILEGES ON *.* TO anel;" > my_init_db/my_grants.sql
```

## See Also

* [Installing and using MariaDB via Docker](installing-and-using-mariadb-via-docker.md)

<sub>_This page is licensed: CC BY-SA / Gnu FDL_</sub>

{% @marketo/form formId="4316" %}
