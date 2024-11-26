# Docker Commands 🐋
**Welcome to the Docker Commands**  



docker images/ docker image ls - List the images in docker images  
docker pull _imagename_ - Downloads the mentioned image(Latest bydefault)  
docker pull _imagename:version_ - Downloads the specific version of mentioned image 
docker history _imagename_ - This will list all the recent changes  
docker rmi _imagename_ - Will delete the image  
docker ps - will show only running containers  
docker ps -a - will show running and created containers  
docker start _containerid/containername_ - will start the container  
docker stop _containerid/containername_ - will stop the container  
docker exec -it _containerid/containername_ /bin/bash - will logs you into the container  
docker --version - gets you the version  
docker login - logs you in to the docker hub  
docker logout - log you out  
docker search _imagename_ - will search about that image  
docker inspect image _imagename_ - will give all information about that image(To run this command image must be installed)  
docker create _imagename_ - will create container  
docker create --name _customname_ _imagename_ - wil create a container with custom name of that image  
docker run --name _customname_ _imagename_ - will create and run the container (create + start), in This bydefault user will get intot the container  
docker run -d _--name _customname__ __imagename_ _- will create and run the container in detached mode  
docker kill __containername/containerid_ _- will kill the container *Forceful shutdonw"  
docker rm containerid/container name - will delete that container  
