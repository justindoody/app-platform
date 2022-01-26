# Overview

Provides basic traefik setup within a Docker image for running various apps and Ansible scripts for configuring docker swarm.

## Deploying

### Secrets & Config

Set the api key secret:
```sh
echo <api_key> | docker secret create CLOUDFLARE_API_KEY -
```

Set the email config:
```sh
echo <email> | docker config create CLOUDFLARE_EMAIL -
```

```sh
docker stack deploy \
-c docker-traefik.yml \
traefik
```

### Traefik Authentication

Traefik is using basic auth to authenticate relying on the file provider which is reading from a docker secret `TRAEFIK_BASIC_AUTH_USERS`.

User/pass combos generated via `echo $(htpasswd -nb user password)`.

See [traefik docs for more](https://doc.traefik.io/traefik/middlewares/basicauth/#usersfile).