# Unbound Docker Image

## About

This is a custom version of the klutchell/unbound image.

Image in Docker Hub: https://hub.docker.com/repository/docker/bdagenais/unbound

## Changes:

- Unbound runs on default port (53) instead of 5053
- Health check for the container checks port 53 instead of 5053
- [My custom config](unbound.conf) is now default

## Use Your Own Config

You may want to use my image to run Unbound on port 53, but don't want to use the rest of my Unbound config. You can mount volume to the container to use your own config.

**With 'docker run':**
```
docker run --name unbound -v /path/to/config.yml:/opt/unbound/etc/unbound bdagenais/unbound
```

**With docker-compose.yml:**
```
services:
  unbound:
    image: bdagenais/unbound
    volumes:
      - '/path/to/config.yml:/opt/unbound/etc/unbound'
```

## Documentation

For all documentation please refer to https://hub.docker.com/r/klutchell/unbound/
