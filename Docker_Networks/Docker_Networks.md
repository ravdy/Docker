# Docker networking

### Docker Networking 

It is a communication passage through which all the isolated containers communicate with each other in various situations to perform the required actions.

Docker networking allows you to attach a container to as many networks as you like. 

### Container Network Model(CNM) 

The IPAM plugin APIs are used to create/delete address pools and allocate/deallocate container IP addresses.   
Network plugin APIs are used to create/delete networks and add/remove containers from networks.

### Network drivers
There are mainly 5 network drivers: 
  1. Bridge
  2. Host 
  3. None 
  4. Overlay 
  5.Macvlan

 #### Bridge: 
 This is a private default internal network created by docker on the host. So, all containers get an internal IP address and these containers can access each other, using this internal IP. The Bridge networks are usually used when your applications run in standalone containers that need to communicate.

#### Host: 
This driver removes the network isolation between the docker host and the docker containers to use the host’s networking directly. So with this, you will not be able to run multiple web containers on the same host, on the same port as the port is now common to all containers in the host network.

#### None: 
In this kind of network, containers are not attached to any network and do not have any access to the external network or other containers. So, this network is used when you want to completely disable the networking stack on a container and, only create a loopback device.

#### Overlay: 
Creates an internal private network that spans across all the nodes participating in the swarm cluster. So, Overlay networks facilitate communication between a swarm service and a standalone container, or between two standalone containers on different Docker Daemons.

#### Macvlan: 
Allows you to assign a MAC address to a container, making it appear as a physical device on your network. Then, the Docker daemon routes traffic to containers by their MAC addresses. Macvlan driver is the best choice when you are expected to be directly connected to the physical network, rather than routed through the Docker host’s network stack.


# Demenastration 

To demenistrate this concept lets start with birdge network. 
You can check networks in docker by using 
```sh

	docker network ls
```
You can see few networks these are default networks. By default all networks associated with bridge network. We can create our own networks. 
1. Create 2 containers in the default bridge network 
```sh 
  docker run -d -it --name nginxappint01 -p 8081:80 nginx 
  docker run -d it --name nginxappint02 -p 8082:80 nginx
```

2. try to access one container with other it should work 
```sh
  docker exec -it nginxappint01 /bin/bash 
  # on container
  sudo apt install iputils-ping
  ping <nginxint02_IP> 
```
3. Create 2 saparate bridge networks 
```sh 
	docker network create --driver=bridge --subnet=192.168.0.0/16 192_network
	docker network create --driver=bridge --subnet=172.28.0.0/16 172_network
```
4. create a container on each network 
```sh 
	docker run -it --name nginxappuat01 --network 192_network -p 8083:80 nginx
	docker run -it --name nginxappuat02 --network 172_network -p 8084:80 nginx
```
5. try to access one container with other. it shouldn't works. 
```sh
  docker exec -it nginxuat01 /bin/bash 
  # on container]
  apt-get update 
  apt install net-tools 
  apt install iputils-ping
  ping <nginxint02_IP> 
```

docker inspect network  <network id>  

docker run -it --name nginxappuat03 --network 172_network -p 8085:80 --ip 172.28.5.100 nginx
