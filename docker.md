# Docker and Docker compose

How to install docker and docker-compose on ubuntu 16.04

* https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04
* https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-16-04

Djano docker setup tutorial:

* https://docs.docker.com/compose/django/#create-a-django-project

Docker compose commands
```
docker-compose up # Builds, (re)creates, starts, and attaches to containers for a service.
docker-compose up -d # Same as above but in background process
docker-compose start # Starts existing containers for a service.
docker-compose down # Stops containers and removes containers, networks, volumes, and images created by up
docker-compose stop # Stops running containers without removing them. They can be started again with docker-compose start
```

Docker commands

https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes

```
docker images -a # list all images
docker rmi $(docker images -a -q) # remove all images

docker images -f dangling=true # list dangling images (images that have no assosiation with tagged image and only use
 free space)
docker rmi $(docker images -f dangling=true -q)

docker ps -a # list all containers

docker rm ID_or_Name ID_or_Name # remove image

docker ps -a -f status=exited # list all container with status exited

docker rm $(docker ps -a -f status=exited -q) # remove all containers with status exited

docker volume ls -f dangling=true # list dangling volumes

docker volume rm $(docker volume ls -f dangling=true -q) # remove all dangling volumes
```

Docker compose commands
```
docker-compose stop [service_name]
docker-compose rm -fv [service_name]
```

ssh to python web service
```
docker exec -ti web /bin/bash
```
