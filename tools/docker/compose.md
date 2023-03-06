# Compose

### File

`docker-compose.yml`

example:

```docker
version: "3.9"  # optional since v1.27.0
services:
  web:
    build: .
    ports:
      - "8000:5000"
    volumes:
      - .:/code
      - logvolume01:/var/log
    depends_on:
      - redis
  redis:
    image: redis
volumes:
  logvolume01: {}
```

### Commands

notes:

**network** - you don't need to specify docker-network using compose. Compose will run containers in new created docker-network

```sh
# up
docker compose up -d
# stop
docker compose stop
# restart
docker compose start
# remove
docker compose down
```
