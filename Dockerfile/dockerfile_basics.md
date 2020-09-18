# Dockerfile basics

FROM 
RUN - (Use RUN command only once, becuase each run command create a new lower)
COPY 
ADD - (To download content inside the container) - Recheck this 
EXPOSE 
CMD  - There can only be one CMD instruction in a Dockerfile. If you list more than one CMD then only the last CMD will take effect.
ENTRYPONT

Create a 1st Docker file to setup tomcat. 
```sh 
	FROM centos
	RUN yum install java-1.8.0-openjdk unzip  wget -y
	RUN mkdir /usr/local/tomcat
	ADD https://apache.cs.utah.edu/tomcat/tomcat-8/v8.5.57/bin/apache-tomcat-8.5.57.tar.gz /usr/local/tomcat
	WORKDIR /usr/local/tomcat/
	RUN tar -xvzf apache-tomcat-8.5.57.tar.gz
	RUN ln -s  /usr/local/tomcat/apache-tomcat-8.5.57/bin/startup.sh /usr/local/bin/startup
	EXPOSE 8080
	CMD ["cd /usr/local/bin/startup"] //this is not working 
```
