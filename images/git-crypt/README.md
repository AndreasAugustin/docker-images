# git-crypt

## Abstract

Contains the [git-crypt][git-crypt] image.

Please check [dev.to/andreasaugustin][dev-to] for details why you should use [git-crypt][git-crypt] for your git repositories.

## Usage

easiest way to use this image is with **docker-compose**

```yaml
# docker-compose.yaml
version: '3.7'

services:
  git-secrets:
    # image from github packages
    # image: ghcr.io/andreasaugustin/git-crypt:main
    # image from dockerhub
    image: andyaugustin/git-crypt:main
    volumes:
      # within . your code should be located on the OS
      - .:/app/
    working_dir: /app/
```

You are now able to use the image with following commands:

```bash
# open terminal with installed commands
docker-compose run git-crypt
```

If you don't need a terminal (e.q. for CI/CD purposes) run

```bash
docker-compose run git-crypt git-crypt <command>
```

[git-crypt]: https://github.com/AGWA/git-crypt
[dev-to]: https://dev.to/andreasaugustin/git-share-secrets-4c60
