# Docker 101
## Build a docker image 
docker build -t nodeapp:v2 .

## Run a docker image in a container named my-node-app-2
docker run --name my-node-app-2 -p 3000:3000 nodeapp 

## Remove a docker container
docker rm <containername>

## Remove a docker image by Name or ID
docker rmi <image_id_or_name>
