# Manage data in Docker
By default all files created inside a container are stored on a writable container layer. This means that:  
The data doesn’t persist when that container no longer exists, and it can be difficult to get the data out of the container if another process needs it.

To list out existing volumes 
  ```sh 
  docker volume ls
  ```
#### to create a container for stateless applications 
  ```sh
  docker run -it --name vtuatjenkins01
  ```
Docker has 3 options for containers to store files in the host machine, so that the files are persisted even after the container stops:

### docker volume types: 
1. anonymous volumes
1. named voluems
1. host volume or bind volumes
 
#### Anonymous Volumes
Create a container with an anonymous volume which is mounted as `/data01` on container. in this case we mention container directory name. On host system it maps to a random-hash directory under /var/lib/docker directory. 
  ```sh 
  docker run -it --name vtwebuat01 -v /data01 nginx /bin/bash
  ```
On Host to verify volume 
  ```sh
  docker volume ls 
  docker inspect <volume_name>
  ```

#### Named Volumes 
Create a container with a named volume name which is mounted as `/data01` on container. You can see volume name as `vtwebuat02_data01_val`
  ```sh 
  docker run -it --name vtwebuat02 -v vtwebuat02_data01_val:/data01 nginx /bin/bash
  ```
Create a named volume then attach volume to a container 
  ```sh 
  docker volume create vtuatweb03_data01_vol
  docker run -it --name vtuatweb03 -v vtuatweb02_data01_vol:/data01 nginx /bin/bash
  ```

Create a named volume with size 
  ```sh
  docker volume create --opt o=size=100m --opt device=/data3 --opt type=btrfs vtuatdb02_data3 // to create volume with size 
  ```

#### Host Volumes 

Create a host volume 
  ```sh 
  mkdir /opt/data02
  docker run -it --name vtwebuat03 -v /opt/data02:/data02 nginx /bin/bash
  ```

### 💡 Help/Suggestions or 🐛 Bugs

Thank you for your interest in contributing to our project. Whether it's a bug report, new feature, correction, or additional documentation or solutions, we greatly value feedback and contributions from our community.


### 🏷️ Metadata

**Level**: 100

