# Docker commands

Login

```bash
docker login

docker login localhost:8080
```

Logout

```bash
docker logout

docker logout localhost:8080
```

Search image

```bash
docker search container_name

docker search container_name -- filter stars=3 --no-trunc busybox
```

Pull image from register

```bash
docker pull container_name

docker pull eon01/container_name localhost:5000/myadmin/container_name
```

Push image from register

```bash
docker push eon01/container_name

docker push eon01/container_name localhost:5000/myadmin/container_name
```

### Containers

Create container

```bash
docker create -t -i eon01/container_name --name container_name
```

Run container (first start)

```bash
docker run -it --name container_name -d eon01/container_name
```

Rename container

```bash
docker rename old_name new_name
```

Remove container

```bash
docker rm container_name
```

Update

```bash
docker update --cpu-shares 512 -m 300M container_name
```

Start

```bash
docker start container_name
```

Stop

```bash
docker stop container_name
```

Restart

```bash
docker restart container_name
```

Pause all process

```bash
docker pause container_name
```

Unpause

```bash
docker unpause container_name
```

Block (before stop)

```bash
docker wait container_name
```

Kill 

```bash
docker kill container_name
```

Connect to contaner

```bash
docker attach container_name
```

Show working containers

```bash
docker ps
docker ps -a
```

Show container logs

```bash
docker logs container_name
```

Info about container

```bash
docker inspect container_name

docker inspect --format '{{ .NetworkSettings.IPAddress }}' $(docker ps -q)
```

Show events

```bash
docker events container_name
```

Show public ports

```bash
docker port container_name
```

Show running container process 

```bash
docker top container_name
```

Show stats

 

```bash
docker stats container_name
```

Show images 

```bash
docker images
```

Create image

```bash
docker build .

docker build URL

docker build - < Dockerfile

docker build - < context.tar.gz

docker build -t eon/infinite .

docker build -f myOtherDockerfile .

curl example.com/remote/Dockerfile | docker build -f - .
```

Remove image

```bash
docker rmi name
```

Show image history

```bash
docker history
```

Create image from container

```bash
docker commit container_name
```

Testing

```bash
docker tag name eon01/name
```

Push image to register

```bash
docker push eon01/name
```

Create network

```bash
docker network create -d overlay MyOverlayNetwork

docker network create -d bridge MyBridgeNetwork

docker network create -d overlay \
  --subnet=192.168.0.0/16 \
  --subnet=192.170.0.0/16 \
  --gateway=192.168.0.100 \
  --gateway=192.170.0.100 \
  --ip-range=192.168.1.0/24 \
  --aux-address="my-router=192.168.1.5" --aux-address="my-switch=192.168.1.6" \
  --aux-address="my-printer=192.170.1.5" --aux-address="my-nas=192.170.1.6" \
  MyOverlayNetwork
```

Remove network

```bash
docker network rm MyOverlayNetwork
```

Show networks

```bash
docker network ls
```

Get info about network

```bash
docker network inspect network_name
```

Remove container

```bash
docker rm container_name
```

Remove container and volume

```bash
docker rm -v container_name
```

Remove all stopped containers

```bash
docker container prune

docker rm `docker ps -a -q`
```

Remove all stopped containers more than 24h

```bash
docker container prune --filter "until=24h"
```

Remove imge

```bash
docker rmi image_name
```

Remove unused images

```bash
docker image prune

docker rmi $(docker images -f dangling=true -q)
```

Remove unused images with tags

```bash
docker image prune -a
```

Remove all images

```bash
docker rmi $(docker images -a -q)
```

Remove all images without tags

```bash
docker rmi -f $(docker images | grep "^<none>" | awk "{print $3}")
```

Stop and remove all containers

```bash
docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)
```
