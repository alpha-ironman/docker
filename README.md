# Docker Commands 🐋
**Welcome to the Docker Commands**  


docker login - login you to docker hub  
docker logout - logout from the login   
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
docker image inspect _imagename_ - will give all information about that image(To run this command image must be installed)  
docker create _imagename_ - will create container  
docker create --name _customname_ _imagename_ - wil create a container with custom name of that image  
docker run --name _customname_ _imagename_ - will create and run the container (create + start), in This bydefault user will get intot the container  
docker run -d --name _customname_ _imagename_ - will create and run the container in detached mode  
docker kill __containername/containerid_ _- will kill the container *Forceful shutdonw"  
docker rm containerid/container name - will delete that container  
docker rename oldcontainername newcontainername - will rename the conatiner  


docker network ls - list of networks  
docker run -d --name customname -p _deviceport:containerport_ _imagename_ - will create the continer with the particular name and keep the traffic to come through port 80 of container and port 8080 of host machine  
docker network inspect bridge - output information about bridge network  
docker network create _networkname_ -  create create with specified name  
docker run -d --name _customname_ --net _(bridge/host/none)_ _imagename_ - This will create a container with specified network type (bydefault: Bridge)  

docker build -t _username/reponame_ . - This will build the docker image with the specifications mentioned in the dockerfile, while running this commadn navigate to rhe location where dockerfile resides and run it, thats why we are using . in cmd.  
docker tag _imagename_ _tagname_ - add tag to the docker image  
docker push _tagname_ - uploads into your source repo (here Docker Hub)  

docker volume ls - list of volumes  
docker volumne inspect _volumeid_ - Detailed information about that volume  
docker volume prune - This will delete the volumes which are not used and this command will delete the unnamed (anonymous) volumes  
docker volume prune _--all_ - This will delete all the volumes even which are named  
docker volume rm _volumeid_ - This will delete the specific volume  
docker volume create _volumename_ -  This will create the volume  
docker run -it --name _containername_ --mount _source=volumename,destination=/foldername_ _imagename_- to create a container with volume (This will mount volume into the sepcified foldername inside the container, bydefault /data is used)  
docker run -it --name _containername_ -v _volumeanme_:/_foldername_ _imagename_ -  Same as above command  
docker run -it --volumes-from container1 --name container2 imagename /bin/bash - will create the a new container (container2) with volume already use in another container(container1)  
docker run -it --name _containername_ -v "$(pwd)":/foldername imagename - will mount the host directory as a data volume  



**DOCKERFILE commands**
**FROM** - Defines the base image used to start the buid process  
**ADD** - Copies the files from a source on the host into the container's own filesystem at the set destination  
**COPY** - Copies the files from a source on the host into the container's filesystem at the set destination  
**CMD** -  Can be used for executing a specific command within the container  
**ENTRYPOINT** - Sets a default application to be used every time a conatiner is created with the image  
**ENV** -  Sets environment variables  
**EXPOSE** -  Associates a specific port to enable networking between the conatiner and to the outside  
**MAINTAINER** - Defines a full name and email address of the image creator  
**RUN** -  is the central executing directive for Dockerfiles  
**USER** -  Sets the UID (Or username) which is to run the container  
**VOLUME** - is used to enable access from the container to a directory on the host machine  
**WORKDIR** - Sets the path where the command, defined with CMD  is to be executed  
**LABEL** -  allows you to add a label to your docker image


**Docker Compose**
Docker Compose is a tool that allows you to define and run multi-container docker applications.

It allows you to define the services, networks and volumes that make up your application in a declarative YAML File, which can then be used to spin up and manage the containers taht make up your application.  

Using Docker Compose, yu can define a grop of related services that can be run together in a single environment, making it easier to manager complex applications with multiple components. for example you can define a web application with a web server, a databse and a chaching layer as seperate services, each running in its own container  

sudo apt install docker-compose - Install docker-compose  
docker-compose --version - tells the version    

service  
  restart  
  image  
  build  
    context  
    dockerfile  
  container_name  
  volumes  
  ports  
  depends_on  
  environment  
  networks  


**Troubleshooting containers**
docker logs _containername_  
docker exec -it containername/containerid sh  - will gets you into container  
_Restart Policies:_

1) **NO** - The default behavior is to not start conatiners automatically
2) **always** - Always restart a stopped conatiner unless the container was stopped explicitly
3) **unless-stopped** - Restart the container unless the conatiner was in stopped state before the docker daemon was stopped
4) **on-failure** - Restart the container if it exited with a non-zero exit code or if the docker daemon restarts  

docker conatiner run --name _containername_ --restart **always** imagename  - to deploy container with restart policy of always  
docker container run --name _containername_ --restart **unless-stopped** imagename - to deploy container with restart policy of unless-stopped  
docker conatiner run --name _containername_ --restart **on-failure** imagename - to deploy container with restart policy of on-failure  
 
