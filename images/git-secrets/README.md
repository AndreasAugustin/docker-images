# git-secrets

## Abstract

Contains the [git-secrets][git-secrets] image.

Please check [dev.to/andreasaugustin][dev-to] for details why you should use [git-secrets][git-secrets] for your git repositories.

## Usage

easiest way to use this image is with **docker-compose**

```yaml
# docker-compose.yaml
version: '3.7'

services:
  git-secrets:
    # image from github packages
    # image: ghcr.io/andreasaugustin/git-secrets:main
    # image from dockerhub
    image: andyaugustin/git-secrets:main
    volumes:
      # within . your code should be located on the OS
      - .:/app/
    working_dir: /app/
```

You are now able to use the image with following commands:

```bash
# open terminal with installed commands
docker-compose run git-secrets
```

If you don't need a terminal (e.q. for CI/CD purposes) run

```bash
docker-compose run git-secrets git-secrets <command>
```

[git-secrets]: https://github.com/awslabs/git-secrets
[dev-to]: https://dev.to/andreasaugustin/git-pretend-accidentally-pushing-git-credentials-11hh
