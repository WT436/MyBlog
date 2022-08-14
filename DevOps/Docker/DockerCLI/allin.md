docker ps -a
docker inspect 83a3806785ad

tạo mới container và image

docker images
docker rmi -f b692a91e4e15
docker history 7b94cda7ffc7

đăng ký : container
docker -v
docker --version 
docker info

docker run nginx

.net 
docker build -f "..\docker_hello_wold\docker_hello_wold\Dockerfile" --force-rm -t dockerhellowold:dev --target base  --label "com.microsoft.created-by=visual-studio" --label "com.microsoft.visual-studio.project-name=docker_hello_wold" "..\docker_hello_wold"

docker run --name dockerhellowold -p 44331:44331 -v C:/dockerhellowold:/var/lib/dockerhellowold -d dockerhellowold:dev

.nginx

docker run -d -p 8080:80 nginx

.ubuntu
docker container run -d -i ubuntu /bin/bash
docker container run -v C:/ubuntu:/var/lib/ubuntu -d -i ubuntu /bin/bash

.volume 
docker volume ls
docker volume rm 0d4c20df3676b0e92d16102376d5c17847d470468e4325b20699dc603fc4a0a6

. networking

docker network create --driver bridge hainam

docker network rm b37a4c2088a4670d5df0b1ef5eee2be02e05e05be20e4064310826fea88d748a

docker run -d --name webserver --network hainam nginx
