## Devpi Dockerfile


This repository contains a modified devpi setup for a
[Docker](https://www.docker.io/) container based on the original
[scrapinghub image](https://index.docker.io/u/scrapinghub/devpi/) with
some changes inspired by [yohanswanepoel/openshift-devpi](https://github.com/yohanswanepoel/openshift-devpi).

## Changes to the original scrapinghub image

- Use python:3.6 instead of python:3 base image
- Use devpi-server==4.3.0 and devpi-client==3.0.0
  (vs. devpi-server>=2.5,<2.6dev and devpi-client>=2.3,<=2.4dev)
- Install devpi-common==3.1.0 and devpi-web==3.2.0 (which enables
  `pip search` functionality
- Run the server with the `restrict-modify` parameter to limit write
  access to the `root` user

## Installation

1. Install [Docker](https://www.docker.io/).

2. Download [build](https://index.docker.io/u/dreizehnelf/docker-devpi-web/)
   from public [Docker Registry](https://index.docker.io/):
   `docker pull dreizehnelf/docker-devpi-web`

   (alternatively, you can build an image from Dockerfile:
   `docker build -t="dreizehnelf/docker-devpi-web" github.com/dreizehnelf/docker-devpi`)

## Usage

### Environment variables

- `DEVPI_PASSWORD`: devpi creates a user named `root` by default, its
  password can be set with this environment variable.
- `DEVPI_MIRROR_CACHE_EXPIRY`: Default to `86400` which is one day.
  Cache expiry time.

### Run `devpi-server`

    `docker run -v $(pwd)/mnt:/mnt -p 3141:3141 -it dreizehnelf/docker-devpi-web:latest`




