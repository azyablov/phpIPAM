# docker compose for phpIPAM

## Intro

The simple way to bring up your phpIPAM in the lab or small network using docker.

## Software Versions

The following phpIPAM/nginx images were tested:

`phpipam/phpipam-www:1.7x`

`phpipam/phpipam-cron:1.7x`

`nginx/1.27.2`


## How to Use

1. Just replace `phpipam.local` with your own domain name.
2. Enroll certificate for your FQDN (server) and put under `./nginx/certs`.
3. Update passwords and username in `docker-compose.yml`.
4. Update `nginx/nginx.conf` file directive `server_name` with server FQDN (in respect of server certificate).
5. Make sure SSL certificate and key file names updated respectively:
```nginx
        # SSL configuration (ensure paths to certificate and key are correct)
        ssl_certificate /etc/nginx/certs/phpipam.local.crt;
        ssl_certificate_key /etc/nginx/certs/phpipam.local.key;
```
6. Create volumes and subnets (allows to get more control):
```sh
docker network create phpipam
docker volume create phpipam-db-data
docker volume create phpipam-logo
docker volume create phpipam-ca
```
6. Follow the standard procedure to automatically install DB (require root password).

## Links

[phpipam-docker](https://github.com/phpipam-docker/phpipam-docker)

[mariadb](https://hub.docker.com/_/mariadb)

[installation](https://phpipam.net/phpipam-installation-on-centos-7/)

[original docker files](https://hub.docker.com/u/phpipam)