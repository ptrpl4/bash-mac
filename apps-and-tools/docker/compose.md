# Compose

### File

`docker-compose.yml`

example:

```yaml
version: '3'
services:
  # uncomment to start one apps with compose file
  # my-app:
  #   image: ci-cd-app:1.0
  #   ports:
  #   - 3000:3000
  mongodb:
    image: mongo
    ports:
      - 27017:27017
    environment:
      - MONGO_INITDB_ROOT_USERNAME=admin
      - MONGO_INITDB_ROOT_PASSWORD=password
    volumes:
      - mongo-data:/data/db
  mongo-express:
    image: mongo-express
    restart: always # fixes MongoNetworkError when mongodb is not ready when mongo-express starts
    ports:
      - 8080:8081
    environment:
      - ME_CONFIG_MONGODB_ADMINUSERNAME=admin
      - ME_CONFIG_MONGODB_ADMINPASSWORD=password
      - ME_CONFIG_MONGODB_SERVER=mongodb
volumes:
  mongo-data:
    driver: local
```

one more

```yaml
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
