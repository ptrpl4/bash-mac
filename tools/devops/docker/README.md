# 🐋 Docker

## Theory

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

image - an artifact/package which includes all necessary information to run the final application

image tag - version of chosen image

* latest

container - running instance of an image

docker registry - image storage. official docker - [https://hub.docker.com/](https://hub.docker.com/)

## Basic commands

## Container operations

### run

creates a new container every time

```bash
# docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
# -d run the container in detached mode (in the background)
# -p 80:80 binds port 80 of the host to port 80 in the container
docker run -d -p 80:80 docker/getting-started

# one more example
docker run -i -t ubuntu bash

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
```

## Image operations

### build

```bash
# list all images
# docker images [OPTIONS] [REPOSITORY[:TAG]]
docker images

# docker pull [OPTIONS] NAME[:TAG|@DIGEST]
docker pull nginx:1.23

# delete image
docker image rm <image-id>

# -t flag tags image. We named the image and we can refer to that.
# . means Docker should look for the Dockerfile in the current directory.
docker build -t getting-started .

# example when file not in root folder
docker build --file build/Dockerfile --tag ptrpl4/repo:ci-cd-test-app-1.0  .
# dont forget "." in the end!
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

## `Dockerfile`

Example

```docker
# syntax=docker/dockerfile:1
FROM node:12-alpine 
# choose image
RUN apk add --no-cache python2 g++ make
WORKDIR /app
# choose workdir
COPY . .
# copy files to workdir
RUN yarn install --production
# install deps
CMD ["node", "src/index.js"]
# run smthg
EXPOSE 3000
# choose port
```

Python + Pipenv example

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
