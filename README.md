# My PiHole + Unbound Implementation

## About

This is a custom implementation of PiHole for Docker with Unbound (provided by klutchell/unbound).

## Usage

1. Download [git](https://git-scm.com/download/linux), [docker](https://docs.docker.com/engine/install/), and [docker-compose](https://docs.docker.com/compose/install/) onto a Raspberry Pi
1. Clone this repo
1. Update .env:
   1. Choose a web password for Pi-Hole (this can be anything)
   1. Add the IP for the host machine
1. Run `docker-compose up -d` inside of the cloned repo's directory
1. Configure your network to use the Raspberry Pi's IP address for DNS

## How it Works

The docker-compose creates a bridge network ("internal") within Docker and assigns a static IP to both the PiHole container and Unbound container.

PiHole is configured to use the Unbound container's IP address on the internal network for DNS queries.

The PiHole container exposes ports 80, 443, and 53 on the same ports on the host machine. Any requests to these 3 ports on the host machine will route the the PiHole container.

## Documentation

PiHole documentation:

- https://hub.docker.com/r/pihole/pihole
- https://docs.pi-hole.net/

Unbound docker image documentation:

- https://hub.docker.com/r/klutchell/unbound/
