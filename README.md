## All commands needed for [docker](https://docs.docker.com/)

### [Learn Docker, Docker Compose, Multi-Container Projects, Deployment and all about Kubernetes from the ground up!](https://www.udemy.com/course/docker-kubernetes-the-practical-guide)

``` 
# run image of node as container
docker run node
```

``` 
# show all processes containers running
docker ps -a
```

```
# expose interactive node terminal from container
docker run -it node
```

```
# to create custom image we need to create a Dockerfile
touch Dockerfile
```

```
# build/rebuild image from Dockerfile in this folder
docker build .
```

```
# run custom docker image
docker run <image_id>
```

```
# list containers running
docker ps 
```

```
# stop running container
docker stop <contianer_name>
```

``` 
# run custom docker image with publish port 3000 of 80 that container exposing
docker run -p 3000:80 <image_id>
# You can see the app running on localhost:3000 in browser
# this will run in foreground
```

``` 
# more info about docker
docker --help
```

``` 
# run the container in the background
docker start <container_id>
```

``` 
# run custom docker image with publish port 3000 of 80 that container exposing in detached mode
docker run -p 3000:80 -d <image_id>
# You can see the app running on localhost:3000 in browser
# this will run in background
```

```
# to attach to the container running in background to see logs
docker attach <container_name>
```

```
# to see logs of the container
docker logs <container_name>
```

```
# to see logs of the container with follow option to attach to the container
docker logs -f <container_name>
```

```
# to start/restart container in attach mode in forground to see logs
docker start -a <container_name>
```

```
# run container in interactive mode to that it can get input from terminal
docker run -it <image_id>
```

```
# to start/restart container in attach interactive mode in forground to see logs
docker start -a -i <container_name>
```

``` 
# to remove container
docker rm <container_name>
# you need to stop the container before removing it
```

```
# to list all images
docker images
```

``` 
# to remove image
docker rmi <image_id>
# you can not remove image if there is a container running from that image or stopped container use it
# container should be removed first
```

```
# remove unused images
docker image prune

# remove unused images including tagged images
docker image prune -a
```

```
# more info about docker run
docker run --help

```

```
# when container stop it will be removed automatically
docker run --rm <image_id>
```

```
# to see info about the image
docker image inspect <image_id>
```

```
# to copy file from host to container and vice versa

docker cp <container_name>:<path_in_container> <path_in_host>

docker cp <path_in_host> <container_name>:<path_in_container>

```

```
# to run container with cusmtom name
docker run --name goalsapp <image_id>
```

```
# to build image with custom name:tag

docker build -t <name:tag> .

docker build -t goals:latest .

docker build -t goals:1 .
```

```

docker login

docker logout

# to share image with others throw docker hub
# note : image should include uername example: ahmedhelalahmed/node-app
docker push <image_name>

# to pull image from docker hub
docker pull <image_name>

# to rename image name
docker tag <old_image_name:tag> <new_image_name:tag>

# pull image from docker
# https://hub.docker.com/layers/academind/node-hello-world/latest/images/sha256-7214ae016bd22c5b1dacfdb8dea50822fe4ec5c365355bf2acc193774cfb412a
docker pull --platform linux/amd64 academind/node-hello-world

# run the image
docker run --platform linux/amd64 academind/node-hello-world

# to run image with platform and publish port 3000
# you can see the app running on localhost:3000 in browser (Hello from inside the very basic Node app!)
docker run -p 3000:3000 -d --platform linux/amd64 academind/node-hello-world
```

