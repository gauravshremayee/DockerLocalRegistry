# DockerLocalRegistry
Create a Local Registry 
docker run -d -p 5001:5001 --restart=always --name registry1 registry:2
docker pull ubuntu:18.04
docker tag ubuntu:18.04 localhost:5000/mylocal-ubuntu
docker push localhost:5000/mylocal-ubuntu
docker image remove ubuntu:18.04
docker image remove localhost:5000/mylocal-ubuntu
docker pull localhost:5000/mylocal-ubuntu
docker images | grep mylocal
