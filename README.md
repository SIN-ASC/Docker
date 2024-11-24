# Docker
Docker is a popular open-source platform that allows developers and system administrators to easily build, ship, and run applications in lightweight, portable, and self-sufficient containers. Containers allow applications to run consistently across various environments, from a developer's local machine to production servers, without the usual "it works on my machine" problems.

## Concepts of Docker
- <b>Containers:</b>
  A container is a lightweight, standalone, and executable package that contains everything needed to run a piece of software: the code, runtime, libraries, and dependencies. Containers are isolated from each other and the host system, but they share the same operating system kernel, which makes them much more efficient than traditional virtual machines.

- <b>Images:</b>
  A Docker image is a snapshot of a container. It includes the application code, libraries, and dependencies required for an application to run. Docker images are used to create containers. Images are read-only, and containers are the running instances of these images.

  Docker images are stored in a Docker registry (e.g., Docker Hub), and they can be pulled from the registry and run on any machine with Docker installed.

- <b>Dockerfile:</b>
  A Dockerfile is a script that contains a series of instructions for building a Docker image. It automates the process of setting up an environment and installing dependencies. A Dockerfile typically contains instructions like FROM (base image), RUN (commands to execute), and COPY (copy files into the container).

- <b>Docker Engine:</b>
The Docker Engine is the core component of Docker. It is a client-server application that consists of:

  - A server (the Docker daemon) that runs in the background and manages containers and images.
  - A REST API that allows interaction with the Docker daemon.
  - A command-line interface (CLI) (docker command) that allows users to communicate with the Docker daemon.

- <b>Docker Compose:</b>
  Docker Compose is a tool that allows you to define and manage multi-container Docker applications. It uses a YAML file (docker-compose.yml) to define services, networks, and volumes, making it easier to manage complex applications composed of multiple containers (e.g., a web server, database, and cache).

## How Docker Works:
- <b>Build:</b>
You write a Dockerfile to specify your application’s dependencies, configuration, and environment. Docker then builds an image from that Dockerfile.

- <b>Ship:</b>
Docker images can be stored in a Docker registry (such as Docker Hub or a private registry). You can share images with others by pushing them to a registry.

- <b>Run:</b>
You run the image as a container on any machine with Docker installed. The container starts with the image as its blueprint, and it runs in isolation with its own file system, network, and processes.

## Why Use Docker?
- <b>Portability:</b>
Containers can run anywhere: on your laptop, in a test environment, or in the cloud. The app runs the same way in all these environments because the container includes everything needed to run it.

- <b>Isolation:</b>
Each container runs independently with its own resources (file system, network, etc.), so there’s no interference between containers, unlike traditional virtual machines.

- <b>Efficiency:</b>
Containers share the host system’s operating system kernel, which means they are much lighter and more resource-efficient than virtual machines. This leads to faster startup times and less overhead.

- <b>Scalability:</b>
Docker makes it easy to scale applications up or down quickly by launching additional containers, often using orchestration tools like Kubernetes or Docker Swarm for container orchestration.

- <b>Consistency:</b>
Docker eliminates the "works on my machine" problem by ensuring that the application runs the same way in every environment. Since the app is packaged with all dependencies in a container, it behaves consistently across different stages of development, testing, and production.

- <b>Microservices Architecture:</b>
Docker is widely used in microservices architecture, where each service is deployed in its own container. This makes managing and scaling applications much easier by keeping services independent and isolated.

## Installation of Docker
- Update system<br>
`sudo dnf update -y`

- Install additional dependencies required for Docker<br>
`sudo dnf install -y yum-utils device-mapper-persistent-data lvm2`

- Add the Docker repository to your system to get the latest version of Docker<br>
`sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo`

- Install Docker<br>
`sudo dnf install -y docker-ce docker-ce-cli containerd.io`

## Docker start and stop
- Start docker<br>
`sudo systemctl start docker`

- Enable docker to start at boot<br>
`sudo systemctl enable docker`

- To check docker service<br>
`sudo systemctl status docker`

- Stop docker<br>
`sudo systemctl stop docker`

## Allow Docker to Run as Non-Root User(Optional)
By default, Docker requires `sudo` to run. If you want to run Docker as a non-root user, you can add your user to the Docker group.

Add your user to the Docker group:<br>
- `sudo usermod -aG docker $USER`<br>
- `newgrp docker`

## Containers and Images

### Containers:
- To see all the running containers<br>
`sudo docker ps`

- To see all the containers (both running and stopped)<br>
`sudo docker ps -a`

- To run a container<br>
  - `sudo docker run hello-world`<br>
  - `sudo docker run -d hello-world` -d to run in the background<br>

- It will start a stop container<br>
`sudo docker start hello-world`

- To pause a container<br>docker pause container id/name<br>
`sudo docker pause hello-world`

- To stop a running container<br>docker stop container id/name<br>
`sudo docker stop hello-world`

- To display the processes of a container<br>docker top container id/name<br>
`sudo docker top hello-world`

- To display stats<br>docker stats container id/name<br>
`sudo docker stats hello-world`

- To remove/delete a container<br>
  docker container rm <container_id><br>
`sudo docker container rm 52411a60a9ea`

- To remove/delete all containers<br>
`sudo docker container prune`<br>It removes all containers including the stopped ones

- To create an image of the container<br>docker commit container id/name<br>
`sudo docker commit hello-world`

### Images:
- To see all the images<br>
`sudo docker image ls`

- To give a new tag to the existing image<br>
`sudo docker tag hello-world:latest my-world:latest`<br> Here 2 different tags will be pointing to the same image
  - hello-world:latest
  - my-world:latest

- To untag an image<br>
`sudo docker image rmi my-world`<br> It will not delete the image, it will just remove the tag my-world from that image

- To remove/delete an image<br>
  docker image rmi <image_id><br>
`sudo docker image rmi d2c94e258dcb -f`<br> -f means forced delete it will be used when a particular image will have multiple tags

## Docker-Compose
Docker compose is "a tool for defining and running complex applications with Docker"
- Run multiple containers from a single config file
- define services, networks and volumes for a Docker application
<br>Why do we use docker compose?<br>
- Because it helps to make our development enivornment repeatable, isolated and fast.
- Then specify images and configurations in a simple YAML/YML file
  - docker-compose.yml

- Command to get it run:<br>
`sudo docker-compose up -d`<br>

- Template
<img src = "Screenshot 2024-11-25 003327.png" width="700" height="400">

- Example
<img src = "Screenshot 2024-11-25 003441.png" width="700" height="400">


## Tomcat
- To pull and run Tomcat<br>
`sudo docker run -d tomcat`<br> Here it will download tomcat to local then run it in a container in the background

- To check if the tomcat is running<br>
`sudo docker ps`

- To go inside the container
`sudo docker exec -it 34c5235e2023 /bin/bash`
