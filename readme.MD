# Docker 101

## Docker Image
A lightweight, standalone, and executable package that includes everything needed to run a piece of software (code, runtime, libraries, dependencies). It's immutable and serves as a blueprint for containers.

## Docker Container
A running instance of a Docker image. It is an isolated, lightweight environment that runs applications consistently across different environments. Containers are ephemeral but can persist data using volumes.

## Docker Commands Step by Step
### 1. Build a docker image 
docker build -t nodeapp:v2 .

### 2. Run a docker image in a container named my-node-app-2
docker run --name my-node-app-2 -p 3000:3000 nodeapp 

### 3. Stop the container ###
docker stop <containerName>

### 3. Remove a docker image by Name or ID
docker rmi <image_id_or_name>

### 4. Remove a docker container
docker rm <containername>

### 5. Run a docker image in a container, and sync changes from local directories and files###
docker run --name my-node-app -p 3000:3000 -v $(pwd):/usr/src/app nodeapp
**Allows to sync all of our stuff to the container, you should stop and start the container**
**You should have the npm packages(modules installed as well)! because we added a bind mount from current directory to the directory in the docker**
-v $(pwd):/usr/src/app 
**means map changes from pwd (current directory to ) **

### 6. Running a container with an anonymous volume ###
**Anonymous volume tells docker to not bind(map)specific directories and packages
in the docker container**
docker run --name my-node-app-6 -p 8000:3000 -v $(pwd):/usr/src/app -v /usr/src/app/node_modules nodeapp:v2

### 7. Proof: inside the container we have node_modules but no in the local directory ###
**Enter the container, and list the directories**
docker exec -it my-node-app-8 /bin/sh

###When you make changes in the local directory, they are synced but doesn't effect the running state of the application for some reason, maybe because they have already been com piled ###

### 8. Build a dev docker image and run it, here we: ###
1. Added the dependency
2. Created a Dockerfile.dev, specifically for image that will listen to any changes
and restart the server 
docker build -t nodeapp:v3 -f Dockerfile.dev .
docker run --name my-node-app-1 -p 8000:3000 -v $(pwd):/usr/src/app -v /usr/src/app/node_modules nodeapp:v3
