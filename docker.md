---
description: Comulative learnings from using Docker at Lossless GmbH
---

# Docker

Docker is the most common container engine and format around. SUpport across major clouds is excellent.

#### Installing Docker

Installing docker is fairly easy. Simply run the following command \(The script will ask for your sudo password if required\)

```bash
curl -sSL https://get.docker.com/ | sh
```

If it prompts that you haven't yet installed curl, do so first and run the command above it again.  
If it complains about SSL try installing the ca-certificates package.

#### Installing Docker-Compose

Docker-Compose makes it easy to setup more complex configurations. It is highly recommended to install it.

```bash
# Get permissions to install Docker Compose
sudo -i

# Download Docker Compose
curl -L https://github.com/docker/compose/releases/download/1.6.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

# Give it executable rights
chmod +x /usr/local/bin/docker-compose

# return to previous rights
exit
```

> **Note:** the latest release for **docker-compose** is: [![GitHub version](https://camo.githubusercontent.com/b2ad4e97f455cf2d56b13edc6d5208581ead1a59/68747470733a2f2f62616467652e667572792e696f2f67682f646f636b6572253246636f6d706f73652e737667)](https://badge.fury.io/gh/docker%2Fcompose)

#### Things that are good to know when building containers

```bash
# adding things to path
ENV PATH /root/.yarn/bin:$PATH
```

**Manage containers and images**

```bash
# Remove all containers
docker rm $(docker ps -a -q)

# Remove containers that are not currently running
docker rm $(docker ps -q -f status=exited)

# Remove all images
docker rmi $(docker images -q)

# Run a seperate shell in a container
docker exec -it my_container_name bash

# attach current shell/bash to running containers
# Note: Please think about executina seperate shell in a container like shown above
$ sudo docker attach loving_heisenberg #by Name

# run bash in any image without using the original command
docker run -it --entrypoint /bin/bash <image>

# find out why a particular service is not running
docker service ps --no-trunc <servicename>
```

#### Docker toolbox

point docker-machine to the right virtualbox instance

```text
docker-machine env --shell cmd default
```

### Tools we wrote at Lossless

#### npmdocker

npmdocker simplifies development of npm modules on your Mac or Linux machine. It comes preinstalled with a lot of handy stuff to make the most of your development experience

**Install it:**

```text
yarn global add npmdocker
```

### Links to learn more

