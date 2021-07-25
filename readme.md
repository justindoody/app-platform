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