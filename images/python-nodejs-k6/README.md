# python-nodejs-k6

## Abstract

Contains the [nikolaik/python-nodejs][nikolaik-python-nodejs] in addition with [k6][k6].

## Usage

easiest way to use this image is with **docker-compose**

```yaml
# docker-compose.yaml
version: '3.7'

services:
  python-nodejs-k6:
    # image from github packages
    # image: ghcr.io/andreasaugustin/git-secrets:main
    # image from dockerhub
    image: andyaugustin/python-nodejs-k6:main
    volumes:
      # within . your code should be located on the OS
      - .:/app/
    working_dir: /app/
```

You are now able to use the image with following commands:

```bash
# open terminal with installed commands
docker-compose run python-nodejs-k6
```

If you don't need a terminal (e.q. for CI/CD purposes) run

```bash
docker-compose run python-nodejs-k6 <command>
```

[nikolaik-python-nodejs]: https://hub.docker.com/r/nikolaik/python-nodejs
[k6]: https://k6.io/
