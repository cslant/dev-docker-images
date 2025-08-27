# dev-docker-images

This repo is to set up the CSlant DEV Images with Docker.

We can use this runner to update all sources for development.

## Docker Hub

[CSlant Docker Hub](https://hub.docker.com/r/cslant)

In this docker repository, we have built the following images:

- [cslant/dev-php56](https://hub.docker.com/r/cslant/dev-php56)
- [cslant/dev-php74](https://hub.docker.com/r/cslant/dev-php74)
- [cslant/dev-php83](https://hub.docker.com/r/cslant/dev-php83)
- [cslant/dev-worker83](https://hub.docker.com/r/cslant/dev-worker83)
- [cslant/dev-php84](https://hub.docker.com/r/cslant/dev-php84)
- [cslant/dev-worker84](https://hub.docker.com/r/cslant/dev-worker84)
- [cslant/dev-mysql57](https://hub.docker.com/r/cslant/dev-mysql57)
- [cslant/dev-mysql](https://hub.docker.com/r/cslant/dev-mysql)
- [cslant/dev-mysql9](https://hub.docker.com/r/cslant/dev-mysql9)
- [cslant/dev-node22](https://hub.docker.com/r/cslant/dev-node22)
- [cslant/dev-node24](https://hub.docker.com/r/cslant/dev-node24)
- [cslant/dev-nginx](https://hub.docker.com/r/cslant/dev-nginx)
- [cslant/dev-postgres](https://hub.docker.com/r/cslant/dev-postgres)
- [cslant/dev-mailhog](https://hub.docker.com/r/cslant/dev-mailhog)

## Prerequisites

First, copy the `.env.example` file to `.env` and update the values.

```bash
envsubst < .env.example > .env
```

If you don't have `envsubst` command, you can use the following command:

```bash
cp .env.example .env
```

### 💻 Start in Mac with arm64

To run as amd64. You need to set the default platform to `linux/amd64`:

```shell
export DOCKER_DEFAULT_PLATFORM=linux/amd64
```
