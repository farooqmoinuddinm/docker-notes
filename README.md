
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

#### Docker commands ####
```
# Below is the command to login to the docker registry or any other registries like: AWS ECR, Dockerhub, Gitlab reigstry etc
docker login 

```
#### Docker build and push example
```
docker build -t [docker-hub-URL]/[your-username]/[image-name]:version .
docker push [docker-hub-URL]/[your-username]/[image-name]:version

```
#### Check running and existed containers
```
docker ps
docker ps -a

```
#### Creat a container
```

docker run -d -p [host-port]:[container-port] --name web-server --network internal-network -v my-vol:/usr/share/nginx/html [image-name]:[version]
docker container logs container-id
docker logs container-id
docker container stop container-id
docker contaier start contaier-id
docker container pause contaier-id
docker exec -it container-id bash
docker inspect container-id
```
#### Docker networking
Docker different network types. 

1. bridge network 
2. host network 
3. overlay network 
4. null
   
```
docker network ls
docker network create roboshop
docker network create --driver=bridge --subnet=192.168.0.0/16 br0
docker inspect netwwork-name
docker network rm roboshop
```

#### Docker volume
volume mount
bind mount
tmpfs mount
```
docker volume create my-vol
docker volume ls
docker volume inspect my-vol
docker volume rm my-vol
docker volume prune

```

#### Docker images
```
docker image ls
docker images
docker image pull [docker-hub-URL]/[your-username]/[image-name]:version
docker image inspect image-name
docker image push [docker-hub-URL]/[your-username]/[image-name]:version
docker image history image-name
docker image build -t image-name .
docker image tag image-name [your-username]/[image-name]:version
docker image rm image-name
docker image list --no-trunc
docker image list --filter dangling=true
docker image list --quiet --filter dangling=true 

```

#### Dockerfile instructions
```
FROM
WORKDIR
ARG
ENV
RUN
COPY
ADD
USER
VOLUME
LABEL
EXPOSE
ENTRYPOINT
CMD

```

