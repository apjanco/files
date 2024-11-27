Ruby JS Python 

Create eScriptorium server in Digial Ocean

- create droplet  8 GB Memory / 160 GB Disk / NYC1 - Ubuntu 24.10 x64
- apt update && apt upgrade

- https://gitlab.com/scripta/escriptorium/-/wikis/docker-install

- git clone https://gitlab.com/scripta/escriptorium.git
- cd escriptorium  
- cp variables.env_example variables.env  

```bash
DOMAIN=escriptorium.pennds.org
SECRET_KEY=...

# change this to a comma separated list of trusted origins
# cf https://docs.djangoproject.com/en/4.0/ref/settings/#csrf-trusted-origins
# exp: http://*.mydomain.com,https://*.mydomain.com
CSRF_TRUSTED_ORIGINS=http://localhost:8080,http://127.0.0.1:8080,https://pennds.org,https://escriptorium.pennds.>
# if using a proxy in front of docker
#USE_X_FORWARDED_HOST=True
#SECURE_PROXY_SSL_HEADER = ('HTTP_X_FORWARDED_PROTO','https')

SITE_NAME=escriptorium
REDIS_HOST=redis
# REDIS_PORT=6379
SQL_HOST=db
SQL_PORT=5432
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=escriptorium
DJANGO_SU_NAME=...
DJANGO_SU_EMAIL=...
DJANGO_SU_PASSWORD=...
DJANGO_FROM_EMAIL=...
FLOWER_BASIC_AUTH=flower:changeme
KRAKEN_TRAINING_LOAD_THREADS=8

``` 

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04

sudo apt install apt-transport-https ca-certificates curl software-properties-common

# Download the docker images to the droplet
docker compose pull 

- docker compose -f docker-compose.yml -f docker-compose.override.yml up -d
