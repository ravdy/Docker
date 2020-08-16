# persist application data using docker volumes

Maintaing data is necessary for the stateful applications eventhough container deleted. In this demonastration we are going to see how can we achive this. 

1. Create a jenkins container 
 ```sh 
 docker run --name vtjenkinsprd01 -p 8080:8080 -p 50000:50000 -v vtjenkinsprd01_jenkins_home_vol:/var/jenkins_home jenkins
 ```
1. Create test job on jenkins console 

1. check for the job in the info in the volume
 ```sh 
 docker volume ls
 docker inspect <volume_name>
 ```
1. Delete docker container 
 ```sh
 docker stop vtjenkinstest01
 docker rm vtjenkinstest01
 ```

1. Create a new container with existing volume name. 
 ```sh
 docker run -d --name vtjenkinsprd02 -p 8090:8080 -p 55000:50000 -v vtjenkinsprd01_jenkins_home_vol:/var/jenkins_home jenkins
 ```

### Using host volumes

1. Create a directory or filesystem and change permssions to 777
 ```sh
 mkdir /opt/jenkins
 chmod 777 /opt/jenkins
 ```
1. Create jenkins server using above directory
 ```sh 
 docker run --name vtjenkinsprd01 -p 9000:8080 -p 60000:50000 -v /opt/jenkins:/var/jenkins_home jenkins
 ```

1. Check for the jenkins data under /opt/jenkins

### 💡 Help/Suggestions or 🐛 Bugs

Thank you for your interest in contributing to our project. Whether it's a bug report, new feature, correction, or additional documentation or solutions, we greatly value feedback and contributions from our community.

### 🏷️ Metadata

**Level**: 100