# nginx-certbot
nginx server with autorenewed certificate


## Pre-requisites
```
docker
docker-compose
configure the DNS record (godaddy: alvarocloud.com) to point to our public IP.
configure the router's NAT to redirect ports 80 and 443 to the server on which we are going to run this repository.
```

Note that the first run of init-letsencrypt.sh may fail, docker bug with cp files. Repeat a second time, and it should work. This only hapens when cp default.conf (first time ever)

## Useful commands
```
docker volume rm nginx_data nginx_log nginx_www
docker volume create nginx_log
docker volume create nginx_data
docker volume create nginx_www

docker network rm nginx_network
docker network create nginx_network
```

## Automatization
crontab every month (At 00:00 on day-of-month 1)
```
0 0 1 * * /opt/nginx-certbot/init-letsencrypt.sh
```

Tener en cuenta que para automatizar es necesario comentar las lineas:
```
# Se comenta para que se pueda automatizar
#if [ -d "$data_path" ]; then
#  read -p "Existing data found for $domains. Continue and replace existing certificate? (y/N) " decision
#  if [ "$decision" != "Y" ] && [ "$decision" != "y" ]; then
#    exit
#  fi
#fi
```
