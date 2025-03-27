Docker commands
1. Build a docker image 
docker build -t nodeapp:v2 .

2. Run a docker image in a container named my-node-app-2
docker run --name my-node-app-2 -p 3000:3000 nodeapp 

3. Remove a docker contains
docker rm <container image>

4. Remove a docker image by Name or ID
docker rmi <image_id_or_name>
