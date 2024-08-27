# 🐋 Docker

A technology that provides virtualisation of isolated and independent containers on a single operating system.

#### links

- docker registry- [https://hub.docker.com/](https://hub.docker.com)
- [web-sandbox](https://labs.play-with-docker.com)
- [guide(ru)](https://my-js.org/docs/guide/docker/) 
- [basics (ru)](https://doka.guide/tools/docker/)

## Theory

### Therms

![](../../aaa-assets/docker-2.jpeg)

images and layers
- **Dockerfile** - set of instructions to build Image from layers. Each instruction creates a layer in the final image.
- Container **Image** - already builded artefact (collection of docker layers)
  includes all necessary information to run a software, including code, runtime, libraries, env vars, config files
- **Registry** - image storage

containers and environment
- **Container** - instance of Container Image
- Container **environment** - context and settings in which a containerised application runs
- **Isolated Docker Network** - network for containers
  containers cloud communicate using container name instead ip:port connections. It automatically used in docker-compose

### Namespaces

Namespaces limiting what containers can see and access.  Containers create namespaces that the particular container will use and have multiple namespaces that present different information about the OS. 

**MNT** namespace limits the mounted file systems a container can use, **USER** namespace is used to isolate users in each container.

### Control groups

Also called cgroups. It is a Linux kernel feature that isolates, prioritizes, and calculates the resource usage (CPU, memory, disk I/O, network, etc.) of a set of processes. 

Control groups can also impose strict limits on usage, ensure that containers use only the resources they need and, if necessary, set limits on the resources a container can use.

### Isolated Union file system

Isolated Union file systems used in containers are stackable. This system helps avoid duplication of data every time you deploy a new container.

### Inside container

layers of images

* linux base image
* application image

if smthg changes - inside container will be updated/changed only image layers with changes

### Docker on macOS

Docker requires a Linux kernel to function, and this requirement is met on macOS using a lightweight virtual machine.

- Docker daemon (`dockerd`) runs inside VM. It manages images, containers, networks, and volumes.
- hypervisor (either Apple’s Hypervisor.framework or qemu) runs the VM that contains the Docker daemon and containers
- Docker images and containers are stored inside the VM, they are managed through the Docker CLI.
- Docker volumes can be mapped to directories on macOS host using the `-v` or `--mount` options in Docker commands.

## Docker commands

Run docker desktop to create socket `~/.docker/docker.sock` for communication with docker daemon.

`open -a Docker` for macOS

### Basics and examples

```bash
# docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

# -d detached(background) mode 
# -p 80:80 binds port 80 of the host to port 80 in the container
docker run -d -p 80:80 docker/getting-started

# --interactive, --tty creating an interactive shell
docker run -i -t ubuntu bash

# --detach, -p bind port, Assign a name to the container
docker run -d -p 3000:3000 --name myapp-new redis:4.0

# mongo example
docker run -d \
    -p 27017:27017 \
    -e MONGO_INITDB_ROOT_USERNAME=admin \
    -e MONGO_INITDB_ROOT_PASSWORD=password \
    --name mongodb \
    --net mongo-network \
    mongo
    
# one more example
docker run -d \
    -p 3000:3000 \
    --name ci-cd-app \
    --net ci-cd-test-project_default \
    ci-cd-app:1.0

# start/stop container
docker stop <the-container-id>
docker start <the-container-id>

# get logs from container (if container runs in -d mode for example)
# docker logs [OPTIONS] CONTAINER
docker logs 87sd7v8sd7f8

#stop and delete container
docker stop <the-container-id>
docker rm <the-container-id>

# check docker network
docker network ls

# exec smthg inside container
docker exec -it 87sd7v8sd7f8 /bin/bash
```

### container commands

```bash
# only create not run container with unique ID and a name
docker container create hello-world
# => 5a30b370e9dfc147f5438380d60ff4b1c43869a752f2ef481b6cf0adb33dae83
# run created container
docker container start c6c7b4c22dfa

# list all include stopped (alias to docker ps)
docker container ls -a
# only running
docker container ls
# show size
docker container ls -s -a
# filter
docker ps --filter status=running

# run(create and run) new container in pseudo-TTY background mode
docker container run -t -d ubuntu # -t allocate a pseudo-teletypewriter
# run in intaractive mode
docker container run -it ubuntu

# interact with running container
docker container exec 9faa5154097e ls

# stop
docker container stop 9faa5154097e

# rm
docker container rm 9faa5154097e # or docker rm
```

### run

flags

```bash
# make session -interactive and allocate -terminal interface for container
docker run -it ubuntu
```

## Image operations

### pull

process

- Docker requests the metadata (manifests) of the specified image. 
- identifies the layers
- Each layer is then downloaded individually (in parallel).
	- If any layer already exists on the local machine, it will be skipped. 
- Each downloaded layer is stored in Docker's local storage.
  The storage location depends on the storage driver being used. with the `overlay2` driver layers are stored under `/var/lib/docker/overlay2/`.
- Once all layers are downloaded and stored, Docker assembles them into a complete image

```bash
# docker pull [OPTIONS] NAME[:TAG|@DIGEST]
docker pull nginx:1.23

# docker images [OPTIONS] [REPOSITORY[:TAG]]
docker images

# delete
docker image rm <image-id>

# -t name the image . look for the Dockerfile in the current directory
docker build -t my-app:1.0 .

# example when file not in root folder
docker build --file build/Dockerfile --tag ci-cd-test-app:1.0  .
# dont forget "." in the end!

# get detailed image info
docker inspect ff095b82
docker inspect ubuntu:v1 --format='{{json .Config}}'
```

### Network

```bash
# check current
docker network

# create new network - docker network create [OPTIONS] NETWORK
docker network create mongo-network
```

### Docker on remote pc

```bash
# connect, login, delete existed, run new in background (example from gitlab ci)
script:
    - ssh -o StrictHostKeyChecking=no -i $SSH_KEY root@138.68.92.11 "
        docker login -u $DOCKER_USER -p $DOCKER_PASSWORD &&
        docker ps -aq | xargs docker stop | xargs docker rm && 
        docker run -d -p 5000:5000 $IMAGE_NAME:$IMAGE_TAG " 
```

## Dockerfile

-  [full reference/](https://docs.docker.com/engine/reference/

Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image.

### Syntax

```dockerfile
# Comment
INSTRUCTION arguments
```

### .dockerignore

exclude files or directories from the build context. This helps avoid sending unwanted files and directories to the builder, improving build speed, especially when using a remote builder.

```dockerignore
# test
node_modules
bar
```
### Examples

```dockerfile
FROM node

ENV MONGO_DB_USERNAME=admin \
    MONGO_DB_PWD=password

RUN mkdir -p /home/app

# copy from host to conainer
COPY ./app /home/app

# set default dir so that next commands executes in /home/app dir
WORKDIR /home/app

# will execute npm install in /home/app because of WORKDIR
RUN npm install

# no need for /home/app/server.js because of WORKDIR
CMD ["node", "server.js"]
```

#### Python + Pipenv example <a href="#remove-a-container-using-the-cli" id="remove-a-container-using-the-cli"></a>

```dockerfile
FROM python:3.9-slim as base

# Setup env
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONFAULTHANDLER 1

FROM base AS python-deps

# Install pipenv and compilation dependencies
RUN pip install pipenv
RUN apt-get update && apt-get install -y --no-install-recommends gcc

# Install python dependencies in /.venv
COPY Pipfile .
COPY Pipfile.lock .
RUN PIPENV_VENV_IN_PROJECT=1 pipenv install --deploy

FROM base AS runtime

# Copy virtual env from python-deps stage
COPY --from=python-deps /.venv /.venv
ENV PATH="/.venv/bin:$PATH"

# Create and switch to a new user
RUN useradd --create-home appuser
WORKDIR /home/appuser
USER appuser

# Install application into container
COPY . .

# Run the application
ENTRYPOINT ["python", "-m", "http.server"]
CMD ["--directory", "directory", "8000"]
```

### Common Dockerfile Instructions

1. FROM:
	- **Purpose**: Specifies the base image
	  `FROM <image>[:<tag>]`
	  `FROM ubuntu:20.04 as base`
2. RUN:  
	- Purpose: Executes a command in a new layer on top of the current image and commits the result.
	  `RUN <command>`
	  `RUN apt-get update && apt-get install -y python3`
```dockerfile
# multiline commands
apt-get update -y \
&& apt-get upgrade -y \
&& apt-get install iputils-ping -y \
&& apt-get install net-tools -y
```
3. COPY:
	- Purpose: Copies files or directories from the host filesystem to the image.
	  `COPY <src> <dest>`
	  `COPY . /app`
4. ADD:
	- Purpose: Similar to `COPY`, but also supports remote URLs and unpacking compressed files.
	  `ADD <src> <dest>`
	  `ADD myapp.tar.gz /app`
5. CMD:
	- Purpose: Specifies the default command to run when a container is started.
	  `CMD ["executable","param1","param2"...]`
	  `CMD ["python3", "app.py"]`
	  or
	  `CMD echo Hello Students. # Run command By default /bin/sh -c`
1. ENTRYPOINT:
	- Purpose: Configures a container to run as an executable.
	  `ENTRYPOINT ["executable","param1","param2"]`
	  `ENTRYPOINT ["python3", "app.py"]`
7. ENV:
	- Purpose: Sets environment variables.
	  `ENV <key>=<value>`
	  `ENV APP_ENV=production`
8. EXPOSE:
	- Purpose: Informs Docker that the container listens on the specified network ports at runtime.
	  `EXPOSE <port> [<port>/<protocol>]`
	  `EXPOSE 80`
9. VOLUME:
	- Purpose: Creates a mount point with the specified path and marks it as holding externally mounted volumes.
	  `VOLUME ["/path/to/dir"]`
	  `VOLUME ["/data"]`
10. WORKDIR:
	- Purpose: Sets the working directory for any subsequent `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD` instructions.
	  `WORKDIR /path/to/workdir`
	  `WORKDIR /app`
1. LABEL:
    - Purpose: define [labels to specify metadata](https://docs.docker.com/engine/reference/builder/#label)
      `LABEL key=value`
      `LABEL "application_environment"="development"`

### run

allows to execute commands or a set of commands during an image build time

#### options

`--mount` option [to create mounts](https://docs.docker.com/engine/reference/builder/#run---mount) that you can access at the build time to bind files, store cache, etc. This option has several types and each provides a specific feature. Among those types are:
- **bind**: binds files or directories to the build container
- **cache**: caches directories for compilers and package managers
- **tmpfs**: for mounting tmpfs in the build container
- **secret**: gives access to secure files
- **ssh**: gives access to SSH keys via SSH agents

```
FROM ubuntu:22.04

LABEL author=HyperUser

RUN --mount=type=cache,target=/var/cache/apt/archives \
  apt-get update -y \
  && apt-get upgrade -y \
  && apt-get install iputils-ping -y \
  && apt-get install net-tools -y

ENTRYPOINT ["/bin/bash"]
```

This configuration can speed up the build process because Docker can use cache from the target directory in case it needs to rebuild the `RUN` layer in later builds.

## Helpers

### run as non-root

- https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```
