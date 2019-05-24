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
$ docker rmi -f $(docker images -a -q)
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

Stop one or more running containers (https://docs.docker.com/engine/reference/commandline/stop/)
```
$ docker stop my_container
```

Fetch the logs of a container (https://docs.docker.com/engine/reference/commandline/logs/)
```
$ docker logs my_container
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

## References

* [Docker Cheat Sheet](https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf)
