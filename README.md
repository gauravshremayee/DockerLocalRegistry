# DockerLocalRegistry

# Tag a image

$docker tag 540a289bab6c nginx:latest

Where 540a289bab6c is docker id found with docker images

# Create a Local Registry 
$docker run -d -p 5000:5001 --restart=always --name registry1 registry:2

$docker pull ubuntu:18.04

$docker tag ubuntu:18.04 localhost:5001/mylocal-ubuntu

$docker push localhost:5001/mylocal-ubuntu

$docker image remove ubuntu:18.04

$docker image remove localhost:5001/mylocal-ubuntu
# Pull from local registry again (mention localhost:5000 otherwise it will fetch from remote ) 

$docker pull localhost:5001/mylocal-ubuntu

$docker images | grep mylocal
