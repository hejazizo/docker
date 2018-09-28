# Manage Docker as a non-root user
The Docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket is owned by the user `root` and other users can only access it using `sudo`. The Docker daemon always runs as the root user.

If you don’t want to preface the `docker` command with `sudo`, create a Unix group called `docker` and add users to it. When the Docker daemon starts, it creates a Unix socket accessible by members of the `docker` group.


1. Create the docker group: `sudo groupadd docker`
2. Add your user to the docker group: `sudo usermod -aG docker $USER`
3. Log out and log back in so that your group membership is re-evaluated.

# Docker Commands

## General
|Command|Description |
|--|--|
|`docker`||
|`docker version`|verified client can talk to engine|
|`docker info`|most config values of engine|
|`docker <command>`|old (still works)|
|`docker <command> <subcommand> options`|new|

## Running Container
|Command|Description |
|--|--|
|`docker container run --publish 80:80 nginx`|running container|
|`docker container run --publish 80:80 --detach nginx`|running container + detach|
|`docker container run --publish 80:80 --detach --name <container> nginx`|running container + detach + name assignment|
|`docker container ls`|list of running containers|
|`docker ps`|list of running containers|
|`docker container ls -a`|list of all created containers so far|
|`docker container logs <container>`|getting logs of container|

Note: `-d` is equat to `--detach`

## Removing Container
|Command|Description |
|--|--|
|`docker container stop <CONTAINER_ID>`|stopping container|
|`docker container start <CONTAINER_ID>`|starting container|
|`docker container rm <container_id>`|removing an stopped container|
|`docker container rm -f <container_id>`|removing a running container (forced)|

|Command|Description |
|--|--|
|`docker top <container>`|process list in one container|

## Environment Variable
|Command|Description |
|--|--|
|`docker top <container>`|displays the processes of `<container>` container|

##
|Command|Description |
|--|--|
|`docker container inspect <container>`|details of one container config(startup config, volumes, networking, etc)|
|`docker container stats`|performance stats for all containers|

## Shell Inside Container
* `-t` (`pseudo-tty`) simulates a real terminal, like what SSH does.
* `-i` (interactive) keep session open to receive terminal input.
* Docker usage: `docker container run [OPTIONS] IMAGE [COMMAND] [ARG...]`

|Command|Description |
|--|--|
|`docker container run -it --name proxy nginx bash`|start new container interactively|

|Command|Description |
|--|--|
|`docker container start -ai ubuntu`|start existing container interactively|

### Run Additional Process in Running Container

|Command|Description |
|--|--|
|`docker container exec -it ubuntu`|run additional command in existing container|

## Docker Networks
|Command|Description |
|--|--|
|`docker container run -p`|run additional command in existing container|
|`docker container port <container>`||

# Images
An image is an ordered collection of root filesystem changes and the corresponding execution parameters for use within a container runtime.