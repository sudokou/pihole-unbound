# Unbound Docker Image

## About

This is a custom version of the klutchell/unbound image. For my use case I needed to run unbound on the default DNS port (53) so I changed the unbound config that ships with this image as well as the health check in the Dockerimage. I also took this opportunity to package my full custom config with this image so I do not need to store the config separately.

Image in Docker Hub: https://hub.docker.com/repository/docker/bdagenais/unbound

## Config changes:

I made the following changes to the unbound config found in klutchell/unbound:

### Modified:

- access-control now only allows access from the internal Docker network I've configured in my docker-compose config (172.30.0.0/16)
- removed interface port so it will use the default port (53)

### Added:

```
server:
    do-ip4: yes
    do-udp: yes
    do-tcp: yes
    prefer-ip6: no
    harden-glue: yes
    harden-dnssec-stripped: yes
    use-caps-for-id: no
    prefetch: yes
    num-threads: 2
    so-rcvbuf: 1m
    private-address: 192.168.0.0/16
    private-address: 10.0.0.0/8
    private-address: 172.30.0.0/16
    qname-minimisation: yes
forward-zone:
    name: "."
    forward-addr: 1.1.1.1@853
    forward-addr: 1.0.0.1@853
    forward-ssl-upstream: yes
```

## Documentation

For all documentation please refer to https://hub.docker.com/r/klutchell/unbound/
