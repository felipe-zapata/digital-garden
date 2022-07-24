# Docker

## Basics

### Volumes

Volumes are the preferred way to persist data in Docker. Easies to back up or migrate than bind mounts. Stored (in linux) in /var/lib/docker/volumes.

> _How do volumes work? When you create a volume, it's stored in a directory on the Docker host. When you mount the volume into a container, this directory is mounted in the container. Volumes are managed by Docker and are isolated from the other core functionalities of the host machine._

Useful commands:

```
docker volume ls // list of volumes
docker volume create volume1 // creates volume1
docker volume inspect volume1 // info about volume1 (including mount point)
```

From: [How to persist data in Docker: Volumes](https://blog.tinystacks.com/how-to-persist-data-in-docker-volumes)

### Bind mounts

> This gives us the main tip in optimizing performance. It’s convenient to use bind mounts at first, and you may find that they are fine for your use case. But if performance becomes a problem, then (1) make sure that you’re only sharing what you need to share, and (2) consider what could be shared in some other way than a bind mount. You have several options for keeping files inside the VM, including a named volume, Linux files in WSL, and the container’s own filesystem: which to use will depend on the use case.

Basically, add this to the docker-compose file

```
    volumes:
      - type: bind
        source: ./jender-theme
        target: /var/www/html/wp-content/themes/jender-theme
```

From: [File Sharing with Docker Desktop](https://www.docker.com/blog/file-sharing-with-docker-desktop/) and [Use bind mounts](https://docs.docker.com/storage/bind-mounts/)

### Images

### Containers

Useful commands:

```
docker rm -f postgresexample // Remove container
docker exec -t -i mycontainer /bin/bash // Enter container filesystem
```

### Networks

## How to's

### How To Setup Your Local Node.js Development Environment Using Docker



From: [How To Setup Your Local Node.js Development Environment Using Docker](https://www.docker.com/blog/how-to-setup-your-local-node-js-development-environment-using-docker/)
