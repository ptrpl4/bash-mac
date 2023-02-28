# 🐋 Docker

## Theory

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

container image - an artifact/package which includes all necessary information to run the container\
image tag - name:version of chosen image\
container - running instance of an image\
registry - image storage. official docker - [https://hub.docker.com/](https://hub.docker.com/)

### Inside container

layers of images

* linux base image
* application image

if smthg changes - inside container will be updated/changed only image layers with changes

## Container operations

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
# docker pull [OPTIONS] NAME[:TAG|@DIGEST]
docker pull nginx:1.23

# docker images [OPTIONS] [REPOSITORY[:TAG]]
docker images

# delete image
docker image rm <image-id>

# -t We named the image and we can refer to that.
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

## Dockerfile

ref - [https://docs.docker.com/engine/reference/builder](https://docs.docker.com/engine/reference/builder)

#### Example

```docker
# syntax=docker/dockerfile:1

# choose image
FROM node:12-alpine 

# choose default direcory for container 
WORKDIR /app

# copy files to workdir
COPY . .

# install deps
RUN yarn install --production

# Final command for run the app
CMD ["node", "src/index.js"]

# choose port
EXPOSE 3000
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
