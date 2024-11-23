# Docker
Docker is a popular open-source platform that allows developers and system administrators to easily build, ship, and run applications in lightweight, portable, and self-sufficient containers. Containers allow applications to run consistently across various environments, from a developer's local machine to production servers, without the usual "it works on my machine" problems.
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
`sudo usermod -aG docker $USER`<br>
`newgrp docker`


