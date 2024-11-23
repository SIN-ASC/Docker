# Docker
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
