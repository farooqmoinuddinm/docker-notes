# docker-notes
This repo is for learning containers and docker

# Basic notes
docker deamon is a service.\
docker engine is actually runs and manage containers.\
docker client is a command line tool to intact with docker engine for creating docker containers, images, etc.\
dockerfile contains instructions to create a docker image.\
docker images are used for creating the docker containers.\
A container is a bundle of Application, Application libraries required to run your application and the minimum system dependencies.\
docker registry contains the docker images, we pull and push images to the docker registry ans share images with others too.\
Containers are light weight, portable and it is easy to share and deploy.

Similar tools like docker: Podman, containerd, rkt, LXC, runc.

Docker image build tools: Dockerfile, Buildah, Kaniko, buildkit.

# Docker installation commands
sudo apt update\
sudo apt install docker.io -y\
systemctl status/start/restart/enabled docker\
sudo usermod -aG docker ubuntu\
docker info\
docker --version

# Docker networking and commands

Below are the network types of docker network 

1. bridge network 
2. host network 
3. overlay network 
4. null 

Default network is bridge network and you can also create a different network type with docker commands.
when we install the docker it will create a docker01 virtual interface. 

docker network ls \
docker network ls --filter driver=bridge \
docker network create simple-network \
docker network inspect simple-network \
docker network rm simple-network \
docker network prune \
docker network connect simple-network container1 \
docker network disconnect simple-network container1 \
docker network create --subnet 192.168.1.0/24 --gateway 192.168.1.1 bridge-farooq \
docker container run -d --name web-server --hostname webserver -p 80:80 --network bridge-farooq -ip 192.168.1.10 farooqmohammed/python-custom \
docker run -itd --network=multi-host-network busybox 


Volumes:
volume mount
bind mount
tmpfs mount

#### Docker commands ####
docker login # is the command to login to the docker registry and We have so many registries: AWS ECR, Dockerhub, Gitlab reigstry etc
# Pull the docker images from docker hub
docker pull nignx (if you do not give any tag, it basically downloads the latest tag image)\
docker pull nginx:16\
docker pull ubuntu:20.04\
# Build your first image
docker build -t farooqmohammed/python-custom:latest .
# Verify the docker image
docker images
docker image ls
# Push the image to docker registry
docker push farooqmohammed/python-custom
# Creating containers commands
docker container run/create\
docker run/create\
docker container run -d --name nignx-server --hostname webserver nginx:latest\
docker ps (it will show only running containers)\
docker ps -a (It will show all the containers)\
docker container inspect nginx-server (you can check the ip address of the container and other useful information of the container)\
docker container rm nginx-server\
docker container run -d --name nignx-server --hostname webserver -p8080:80 nginx:latest\
docker container run -d --name ubuntu-server ubuntu:20.04 (this container will existed because it has not running any application, run this you need to run the container like below)\
docker container -itd --name ubuntu-server ubuntu:20.04


# Login to the container
docker exec -it nginx-server bash

# Docker file commands
Here are all the commands that we can use in the Dockerfile.\
Comments \
FROM \
CMD \
ENTRYPOINT \
WORKDIR \
ENV \
COPY \
LABEL \
RUN \
ADD \
.dockerignore \
ARG \
EXPOSE \
USER \
VOLUME
