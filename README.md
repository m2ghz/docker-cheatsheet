# docker-cheatsheet
- first install docker with this link:
https://docs.docker.com/get-docker/

pull specific image
show docker version that image created with it
what ports does image exposes

save image in tar file
remove image and add tar file as a another name in local docker hub

run container with image imported in last step and expose 8081 port
docker run -d -p 8081:80 nginx:v1.20.0-test

docker-proxy:
forward port traffic from host to container 

Dangling images:
image without name and tag 

How to remove dangling image:
docker image prune

when kill container send sigterm to that container and container exit with code 137

run container from alpine image and install nginx on it and save(commit) image from it
docker commit alp alnginx:latest

when container paused, all state saved in memory but that container didn't access to cpu

for save container id we have to options:
first: with docker exec <container-name> hostname > filename.cid
second: with  docker container inspect <container-name> | jq .[0].Config.Hostname > filename.cid
 
for limit container in ram & swap and cpu follow these steps:
first you need enable swap limit feature
For set swap limit follow these step:
- add GRUB_CMDLINE_LINUX_DEFAULT="cgroup_enable=memory swapaccount=1" /etc/default/grub
- update-grub
- reboot
     options       				value
 --memory 512M   			 limit ram 
 --memory-swap 768M  			 limit swap (swap-ram)=swap-needed
 --cpu-period 100000 --cpu-quota 50000   limit cpu with 0.5 core (alternative cpus 0.5)
 --cpuset-cpus 0 			 specify cpu affinity

if you need add enviornment variable, you can add it with -e option when you want create container 
docker run --name alpp -dit -e CLASS=dws -e NAME=matthew alpine:latest /bin/sh

for mount directory use -v with run container

for change working directory you can use -w </directory> option with run container

if you have a problem feel free to ask questions.

[@dwsclass](https://github.com/dwsclass) dws-ops-004-docker
[@dwsclass](https://github.com/dwsclass) dws-ops-005-docker
