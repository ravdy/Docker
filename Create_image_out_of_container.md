# Create Image out of a Container
Usually we create a Image out of Dockerfile. But we can still create an image out of a container

### Pre-requisites
1. Docker environment 
2. dockerhub account  
### Procedure

Steps we are following 
1. pull nginx image
2. Create a container 
3. Do some changes on the container
4. Create an image using container
5. Push image to hub.docker.com
6. Remove container and image
7. create container using our custom image
8. We could able to see changes 

### Demonstration 

1. Pull nginx docker image
	```sh
	docker pull nginx:latest
	```

1. Create a container using nginx image
	```sh
	docker run -dt --name vtproxyuat01 -p 8080:80 nginx:latest 
	docker exec -it vtproxyuat01 /bin/bash
		or
	docker run -it --name vtproxyuat01 -p 8080:80 nginx:latest /bin/bash
	```

1. Modify index.html file on container 
	```sh
	cat >> /user/share/nginx/html/index.html
    ```
1. Create an image out of the container
	```sh
	docker commit vtproxyuat01 <docker_account_id>/vtproxyimage:<tage_name>
	```
1. Push image to dockerhub account
	```sh
	docker push <docker_account_id>/vtproxyimage:<tage_name>
	```

1. Remove containers and images
	```sh 
	docker stop vtproxyuat01
	docker rm vtproxyuat01
	docker system prune --all // to remove all stopped containers and unused images 
	```

1. Create a container using image which we pushed to dockerhub.
	```sh
	docker run -it --name vtproxyuat02 -p 8080:80 <docker_account_id>/vtproxyimage:<tage_name> /bin/bash
	```

1. Check for the content in the file. We could see same our changes. 

### 💡 Help/Suggestions or 🐛 Bugs

Thank you for your interest in contributing to our project. Whether it's a bug report, new feature, correction, or additional documentation or solutions, we greatly value feedback and contributions from our community.

### 🏷️ Metadata

**Level**: 100