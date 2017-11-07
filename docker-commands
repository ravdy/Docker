https://storebits.docker.com/ee/rhel/sub-0264dcdc-7e65-41e9-b187-09ad62c1ca2b/rhel/7/x86_64/stable-17.03/Packages/

wget https://storebits.docker.com/ee/rhel/sub-0264dcdc-7e65-41e9-b187-09ad62c1ca2b/rhel/7/x86_64/stable-17.03/Packages/docker-ee-17.03.0.ee.1-1.el7.centos.x86_64.rpm


yum install -y libtool-ltdl.x86_64 libseccomp.x86_64


wget https://storebits.docker.com/ee/rhel/sub-0264dcdc-7e65-41e9-b187-09ad62c1ca2b/rhel/7/x86_64/stable-17.03/Packages/docker-ee-selinux-17.03.0.ee.1-1.el7.centos.noarch.rpm


rpm -Uvh docker-ee-selinux-17.03.0.ee.1-1.el7.centos.noarch.rpm

rpm -Uvh docker-ee-17.03.0.ee.1-1.el7.centos.x86_64.rpm

docker version
docker --version

docker image ls
docker pull <image-id> 
docker pull hello-world
docker image ls
docker info
docker image history
docker container run 05a3bd381fc2
docker container ls
docker container ls -a
docker search centos:centos7.4.1708

docker container run -i -t --name centOS 5076a7d1a386

docker pull tomcat

docker image pull tomcat


docker container run -d -p 8080:80 --name apache-3 3eb9a51149d5

docker container start 200c2ae86214
docker container stop 200c2ae86214
docker container pause 200c2ae86214
docker container unpause 200c2ae86214
docker container kill 9096b2c434ba
docker container rm 03ad64d46c5a 790a25acc739
docker container rm -f 790a25acc739

docker container attach 5076a7d1a386
docker container stats 9096b2c434ba

docker container logs 9096b2c434ba
docker container top c26462e3656d

docker build -t <image-name>:<tag> .
docker image tag apache3 arsr319/apache3
docker push arsr319/apache3

docker container run -d -t 9090:80 --name apache3 e5502d046e81
docker image history be775364543a
docker image rm becd5bf4a39d
docker rm a2342d66993a

docker run -d -p 6000:5000 --restart=always --name myregistry registry:2

docker image tag mycentos:7.3 arsr319/mycentos

docker network inspect bridge
docker network ls
docker network create mynetwork
docker network inspect mynetwork
docker network create mynetwork --driver=host or nune
docker image pull russmckendrick/moby-counter
docker contaner run -d --name myredisdb --network mynetwork redis:alpine
docker container run -d --name myapp-counter --network mynetwork -p 8080:80 <image-id>
docker container ps -a | awk '{print $1}' | docker container rm -f
docker volume ls
docker volume myvolume
docker volume inspect myvolume
docker container run -d --name redies --volume /opt/data:/data --network <network> <image-id>

install docker compose

sudo curl -L https://github.com/docker/compose/releases/download/1.16.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose

chmod +x  /usr/local/bin/docker-compose
docker-compose --version

docker-compose up
docker-compose up -d
docker-compose ps
docker-compose stop
docker-compose rm
docker-compose config

docker-compose up --build


Docker Swam 

TCP port is 2377 and 2375
TCP/UDP 7946
UDP 4789


docker swarm init --advertise-addr <IP-address>

docker swarm join --token SWMTKN-1-0peuazxju17eer2a0dom3acjv1t1vcimo7ir2sfgilnyoxdjnd-b90hq1eum9dpqqw0nnhgr4qq7  192.168.1.182:2377

docker network create --driver overlay --subnet=10.0.9.0/24 demo-net

docker service create --name master-clone --network demo-net --replicas 2 ubuntu

docker 
docker node ls
docker service ls
docker stack ls


docker pull pattonwebz/wordpress-php7-1-apache-memcached

pattonwebz/wordpress-php7-1-apache-memcached

pattonwebz/docker-wpcli

docker swarm join --token <SWMTKN> <Master-IP>


version: "3"

services:
  sampleapp:
    image: sampleapp
    deploy:
      replicas: 4
      resources: 
        limits:
          cpus: "0.1"
          memory: 50M
      restart_policy:
        condition: on-failure
   ports:
     - "80:80"
   networks:
     - network-sample
networks:
  network-sample:

------------------------------

docker stack deploy -c docker-compose.yml pythonapp

docker stack rm demo3

docker inspect 
docker  exec -it f68f8d5ec87d bash









docker network create --opt encrypted --driver overlay my-multi-host-network
docker network rm 


docker volume inspect db_data




