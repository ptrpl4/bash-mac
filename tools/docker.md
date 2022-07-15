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

## Remove a container <a href="#remove-a-container-using-the-cli" id="remove-a-container-using-the-cli"></a>

```bash
docker ps # get id
docker stop <the-container-id>
docker rm <the-container-id>
```
