# docker compose for phpIPAM

## Software Versions

The following phpIPAM images were tested:

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
6. Follow the standard procedure to automatically install DB (require root password).

## Links
[phpipam-docker](https://github.com/phpipam-docker/phpipam-docker)
[mariadb](https://hub.docker.com/_/mariadb)
[installation](https://phpipam.net/phpipam-installation-on-centos-7/)