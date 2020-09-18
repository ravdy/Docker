# Docker Introduction
## Why Docker
For many years now, enterprise software has typically been deployed either on “bare metal” (i.e. installed on an operating system that has complete control over the underlying hardware) or in a virtual machine (i.e. installed on an operating system that shares the underlying hardware with other “guest” operating systems).
Virtual machines also helped cut costs, because more VMs could be consolidated onto fewer physical machines. Legacy systems running older applications could be turned into VMs and physically decommissioned to save even more money.

VMs are not able to deliver the kind of speed, agility, and savings that fast-moving businesses are demanding.

Docker enables more efficient use of system resources
	Instances of containerized apps use far less memory than virtual machines, they start up and stop more quickly
	Save on costs of software licenses, because you need many fewer operating system instances to run the same workloads.

Docker enables faster software delivery cycles

Docker shines for micro services architecture

## Docker basic Commands
```sh
docker version
docker info 
docker images 
docker ps 
docker ps -a 
docker stats 
docker run -it centos /bin/bash (i - interactive t - terminal)
docker run -d -t centos /bin/bash 
docker exec -it centos 
	(Ctrl +pq to come out from container )
docker stop <container_name>
docker start <container_name>
```

docker images and containers stored under /var/lib/docker
```sh 
docker  run -d -t --name <name> --hostname <container_hostname> <image_name> 
example: docker run -d -t --name nginxserver --hostname nginxpod nginx
 
docker rm <contaienr> 
```

### Port forwarding 
```sh
docker run -d -t --name nginx -p 8080:80 nginx
```

inside a container of nginx got to /user/share/nginx/html location to update index.html

```sh
 docker commit <contaner_ID> image_name:V1  - to create image out of container 
 docker login <Docker_hub_URL>:<port>
```
#Docker Image
 Docker Containers are nothing but the runtime instance of Docker Image.
`
