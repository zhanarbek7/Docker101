# Docker 101

## Docker Image
A lightweight, standalone, and executable package that includes everything needed to run a piece of software (code, runtime, libraries, dependencies). It's immutable and serves as a blueprint for containers.

## Docker Container
A running instance of a Docker image. It is an isolated, lightweight environment that runs applications consistently across different environments. Containers are ephemeral but can persist data using volumes.

## Docker Commands
### Build a docker image 
docker build -t nodeapp:v2 .

### Run a docker image in a container named my-node-app-2
docker run --name my-node-app-2 -p 3000:3000 nodeapp 

### Remove a docker container
docker rm <containername>

### Remove a docker image by Name or ID
docker rmi <image_id_or_name>

### Run a docker image in a container, and sync changes from local directories and files
docker run --name my-node-app -p 3000:3000 -v $(pwd):/usr/src/app nodeapp
**Allows to sync all of our stuff to the container, you should stop and start the container**
**You should have the npm packages(modules installed as well)! because we added a bind mount from current directory to the directory in the docker**
-v $(pwd):/usr/src/app 
**means map changes from pwd (current directory to ) **
