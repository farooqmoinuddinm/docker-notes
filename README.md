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

Network: Bridge, Host, None, Overlay, Macvlan\
docker network ls # it will list all the nework types available\
docker network rm bridge\
docker network inspect bridge\
if whilte creating any container by default it uses the docker0 bridge network.


Volumes:
volume mount
bind mount
tmpfs mount

#### Docker commands ####
docker login # is the command to login to the docker registry and We have so many registries: AWS ECR, Dockerhub, Gitlab reigstry etc
# Pull the docker images from docker hub
docker pull nignx (if you do not give any tag, it basically downloads the latest tag image)
docker pull nginx:16
docker pull ubuntu:20.04
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
docker container inspect nginx-server (you can check the ip address of the container and other useful information of the container)
# Login to the container
docker exec -it nginx-server bash

