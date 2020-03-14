# Docker Cheat Sheet

## Images

List images (https://docs.docker.com/engine/reference/commandline/images/)
```
$ docker images -a
```

Build an image from a Dockerfile (https://docs.docker.com/engine/reference/commandline/build/)
```
$ docker build .
```

Remove one or more images (https://docs.docker.com/engine/reference/commandline/rmi/)
```
$ docker rmi -f my_image
```

Remove unused data (https://docs.docker.com/engine/reference/commandline/system_prune/)
```
$ docker system prune
```

Remove all images
```
$ docker system prune --all
```

## Networks

Create a network (https://docs.docker.com/engine/reference/commandline/network_create/)
```
$ docker network create mynetwork
```

List networks (https://docs.docker.com/engine/reference/commandline/network_ls/)
```
$ docker network ls
```

Remove all unused networks (https://docs.docker.com/engine/reference/commandline/network_prune/)
```
$ docker network prune
```

Remove one or more networks (https://docs.docker.com/engine/reference/commandline/network_rm/)
```
$ docker network rm mynetwork
```

## Containers

List containers (https://docs.docker.com/engine/reference/commandline/ps/)
```
$ docker ps -a
```

Run a command in a new container (https://docs.docker.com/engine/reference/commandline/run/)
```
$ docker run -d -p 8080:8080 my_image
```

Run a bash shell in a container (https://docs.docker.com/engine/reference/commandline/exec/)
```
$ docker exec -it <container_name> /bin/bash
```

To exit bash shell in a container
```
$ exit
```

Stop one or more running containers (https://docs.docker.com/engine/reference/commandline/stop/)
```
$ docker stop my_container
```

Fetch the logs of a container (https://docs.docker.com/engine/reference/commandline/logs/)
```
$ docker logs my_container
```

Stop all containers
```
$ docker stop $(docker ps -a -q)
```

## Compose

Builds, (re)creates, starts, and attaches to containers for a service. (https://docs.docker.com/compose/reference/up/)
```
$ docker-compose up -d
```

Stops containers and removes containers, networks, volumes, and images created by up. (https://docs.docker.com/compose/reference/down/)
```
$ docker-compose down
```

Starts existing containers for a service. (https://docs.docker.com/compose/reference/start/)
```
$ docker-compose start
```

Stops running containers without removing them. (https://docs.docker.com/compose/reference/stop/)
```
$ docker-compose stop
```

Displays log output from services. (https://docs.docker.com/compose/reference/logs/)
```
$ docker-compose logs my_container
```

## References

* [Docker Cheat Sheet](https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf)
