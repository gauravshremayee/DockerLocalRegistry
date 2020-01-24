# DockerLocalRegistry

# Tag a image

$docker tag 540a289bab6c nginx:latest

Where 540a289bab6c is docker id found with docker images

# Create a Local Registry 
#5000 is default port within which container runs

$docker run -d -p 5000:5000 --restart=always --name registry1 registry:2

     if above doesn't work try similar to below:

     docker run -d -p 5007:5000 --restart=always --name registry11 registry:2
     
     

$docker pull ubuntu:18.04

$docker tag ubuntu:18.04 localhost:5000/mylocal-ubuntu

$docker push localhost:5000/mylocal-ubuntu

$docker image remove ubuntu:18.04

$docker image remove localhost:5001/mylocal-ubuntu
# Pull from local registry again (mention localhost:5000 otherwise it will fetch from remote ) 

Note: export DOCKER_CONTENT_TRUST=0 Otherwise image might not be pulled
$docker pull localhost:5000/mylocal-ubuntu

$docker images | grep mylocal

# Customize the published port

If you are already using port 5000, or you want to run multiple local registries to separate areas of concern, you can customize the registry’s port settings. This example runs the registry on port 5001 and also names it registry-test. Remember, the first part of the -p value is the host port and the second part is the port within the container. Within the container, the registry listens on port 5000 by default.

$ docker run -d \
  -p 5001:5000 \
  --name registry-test \
  registry:2
If you want to change the port the registry listens on within the container, you can use the environment variable REGISTRY_HTTP_ADDR to change it. This command causes the registry to listen on port 5001 within the container:

$ docker run -d \
  -e REGISTRY_HTTP_ADDR=0.0.0.0:5001 \
  -p 5001:5001 \
  --name registry-test \
  registry:2
