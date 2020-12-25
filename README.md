# Miniflux via docker

For this project to work, you will have to also install the `traefik-docker` project available [here](https://github.com/m1rkwood/traefik-docker).

## Setup your DNS

Setup your subdomain so that when you're ready, it's already pointing to the right direction. Simply go to your DNS provider, and create a `A` record with the information needed:

```
Type: A Record
Host:
Value: IP-OF-YOUR-SERVER
TTL:
```

For `Host`, choose whatever subdomain you want to host at.
For `TTL`, I used the lowest available or `Automatic`

## Envionment

Duplicate the `.env.template` and rename it to `.env`
In the `.env` file, add the information necessary, generate strong passwords for ADMIN_PASSWORD & POSTGRES_PASSWORD.

## Run the container

```
docker-compose up -d
```

## Update miniflux

```
docker-compose build --pull
docker-compose up -d
```
