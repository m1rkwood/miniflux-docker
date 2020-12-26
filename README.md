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

### Backup the database automatically

You can add a cronjob to backup your database regularly.  
On the host server, run `crontab -u <username> -e` and add the following:

```
0 8 * * 2 docker exec miniflux-postgres pg_dump -U <POSTGRES_USER> <DATABASE_NAME> > <PATH_TO_BACKUPS>/backups/backup_`date +%Y%m%d%H%M%S`.sql
```
