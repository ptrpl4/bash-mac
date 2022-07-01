# 🐋 Docker

## Basic commands

run

```bash
docker run -d -p 80:80 docker/getting-started
# -d - run the container in detached mode (in the background)
# -p 80:80 - map port 80 of the host to port 80 in the container
# docker/getting-started - the image to use
docker run -i -t ubuntu bash # one more example
```

build

```bash
docker build -t getting-started .
# -t flag tags image. We named the image and we can refer to that.
# . means Docker should look for the Dockerfile in the current directory.
```

## `Dockerfile`

`Example`

```docker
# syntax=docker/dockerfile:1
FROM node:12-alpine
RUN apk add --no-cache python2 g++ make
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```

## Remove a container <a href="#remove-a-container-using-the-cli" id="remove-a-container-using-the-cli"></a>

```bash
docker ps # get id
docker stop <the-container-id>
docker rm <the-container-id>
```
