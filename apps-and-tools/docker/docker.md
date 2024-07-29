# 🐋 Docker

A technology that provides virtualisation of isolated and independent containers on a single operating system.

#### links

- docker registry- [https://hub.docker.com/](https://hub.docker.com)

## Theory

### Therms

![](../../aaa-assets/docker-2.jpeg)

- Container **Image** - an artefact(file) which includes all necessary information to run a piece of software, including the code, runtime, libraries, environment variables, and configuration files
- **Registry** - image storage
- **Dockerfile** - set of instructions how to build Image. Each instruction creates a layer in the image, contributing to the final structure of the container environment  
- **Container** - running instances of Container Image
- Container **environment** - context and settings in which a containerized application runs
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

## Docker commands

### Basics and examples

```bash
# docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
# -d run the container in detached(background) mode 
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

# docker ps [OPTIONS] 
# -a include stopped
docker ps -a 

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

# list all
docker container ls -a
# only running
docker container ls

# run(create and run) new container in pseudo-TTY background mode
docker container run -t -d ubuntu # -t allocate a pseudo-teletypewriter
# run in intaractive mode
docker container run -it ubuntu

# interact with running container
docker container exec 9faa5154097e ls


# stop
docker container stop 9faa5154097e

# rm
docker container rm 9faa5154097e
```

### run

flags

```bash
# make session -interactive and allocate -terminal interface for container
docker run -it ubuntu
```

## Image operations

```bash
# docker pull [OPTIONS] NAME[:TAG|@DIGEST]
docker pull nginx:1.23

# docker images [OPTIONS] [REPOSITORY[:TAG]]
docker images

# delete image
docker image rm <image-id>

# -t name the image . look for the Dockerfile in the current directory
docker build -t my-app:1.0 .

# example when file not in root folder
docker build --file build/Dockerfile --tag ci-cd-test-app:1.0  .
# dont forget "." in the end!
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

ref - [https://docs.docker.com/engine/reference/builder](https://docs.docker.com/engine/reference/builder)

#### Example

```docker
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

```docker
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
	- **Purpose**: Specifies the base image to use for the subsequent instructions.
	- **Syntax**: 
	- `FROM <image>[:<tag>]`
	- `FROM ubuntu:20.04`
2. RUN:  
	- **Purpose**: Executes a command in a new layer on top of the current image and commits the result.
	- **Syntax**: `RUN <command>`
	- `RUN apt-get update && apt-get install -y python3`
3. **COPY**:
	- **Purpose**: Copies files or directories from the host filesystem to the image.
	- **Syntax**: `COPY <src> <dest>`
	- `COPY . /app`
4. **ADD**:
	- **Purpose**: Similar to `COPY`, but also supports remote URLs and unpacking compressed files.
	- **Syntax**: `ADD <src> <dest>`
	- `ADD myapp.tar.gz /app`
5. **CMD**:
	- **Purpose**: Specifies the default command to run when a container is started.
	- **Syntax**: `CMD ["executable","param1","param2"]`
	- `CMD ["python3", "app.py"]`
6. **ENTRYPOINT**:
	- **Purpose**: Configures a container to run as an executable.
	- **Syntax**: `ENTRYPOINT ["executable","param1","param2"]`
	- `ENTRYPOINT ["python3", "app.py"]`
7. **ENV**:
	- **Purpose**: Sets environment variables.
	- **Syntax**: `ENV <key>=<value>`
	- `ENV APP_ENV=production`
8. **EXPOSE**:
	- **Purpose**: Informs Docker that the container listens on the specified network ports at runtime.
	- **Syntax**: `EXPOSE <port> [<port>/<protocol>]`
	- `EXPOSE 80`
9. **VOLUME**:
	- **Purpose**: Creates a mount point with the specified path and marks it as holding externally mounted volumes.
	- **Syntax**: `VOLUME ["/path/to/dir"]`
	- `VOLUME ["/data"]`
10. **WORKDIR**:
	- **Purpose**: Sets the working directory for any subsequent `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD` instructions.
	- **Syntax**: `WORKDIR /path/to/workdir`
	- `WORKDIR /app`

## Helpers

### run as non-root

- https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```
