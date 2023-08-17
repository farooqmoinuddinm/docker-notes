# Basic notes
docker deamon is a service.\
docker engine is actually runs and manage containers.\
docker client is a command line tool to intact with docker engine for creating docker containers, images, etc.\
dockerfile contains instructions to create a docker image.\
docker images are used for creating the docker containers.\
A container is a bundle of Application, Application libraries required to run your application and the minimum system dependencies.\
docker registry contains the docker images, we pull and push images to the docker registry ans share images with others too.\
Containers are light weight, portable and it is easy to share and deploy.

Container Run times: \
Docker \
Podman \
containerd \
rkt \
LXC \
runc

Container image build tools: \
  Docker \
  Buildah \
  Kaniko \
  buildkit

# Docker installation commands on ubuntu server
```
sudo apt update
sudo apt install docker.io -y
systemctl status/start/restart/enabled docker
sudo usermod -aG docker ubuntu
docker info
docker --version
```
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
#### Create and operate containers
```

# Create a container with different options
docker run -d -p [host-port]:[container-port] --name web-server --network internal-network -v my-vol:/usr/share/nginx/html [image-name]:[version]
# check the container logs for any application errors and issues
docker container logs container-id
docker logs container-id
# Stop, start and pause the container
docker container stop container-id
docker contaier start contaier-id
docker restart container-id
docker container pause contaier-id
docker unpause contaier-id

# Login to the container for any troubleshooing and check the information
docker exec -it container-id bash
docker exec <container_id_or_name> netstat -tuln
docker inspect container-id
# Copy data from host to container
docker cp <local_path> <container_id_or_name>:<container_path>
# Copy data from container to host
docker cp <container_id_or_name>:<container_path> <local_path>
# kill the container
docker kill container-id
# check the container resource usage
docker top container-id

docker diff conainer-id
docker commit container image

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
volume mount \
bind mount \
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
# list all the images with below command
docker image ls
docker images

# print only image id's
docker image ls -q

# remove or delete the single image
docker image rm image-name

# removing all the images at a time
docker image rm $(docker image ls -q)

# pull the image from the remote registry
docker image pull [docker-hub-URL]/[your-username]/[image-name]:version

# inspect the image
docker image inspect image-name

# push the image to container registry
docker image push [docker-hub-URL]/[your-username]/[image-name]:version

# Check the image history
docker image history image-name

# build the images with below command
docker image build -t image-name .

# Tag the image
docker image tag image-name [your-username]/[image-name]:version

docker image list --no-trunc
docker image list --filter dangling=true
docker image list --quiet --filter dangling=true
docker image prune
docker image prune -f

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
