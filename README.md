# Docker
## Installation of Docker
- Update system
`sudo dnf update -y`

- Install additional dependencies required for Docker
`sudo dnf install -y yum-utils device-mapper-persistent-data lvm2`

- Add the Docker repository to your system to get the latest version of Docker
`sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo`

- Install Docker
`sudo dnf install -y docker-ce docker-ce-cli containerd.io`

## Docker start and stop
- Start docker
`sudo systemctl start docker`

- Enable docker to start at boot
`sudo systemctl enable docker`

- To check docker service
`sudo systemctl status docker`

- Stop docker
`sudo systemctl stop docker`
