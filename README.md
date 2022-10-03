# nginx-certbot
nginx server with autorenewed certificate


## Pre-requisitos
```
docker
docker-compose
configurar el registro DNS (godaddy: alvarocloud.com) para que apunte nuestra IP pública.
configurar el NAT del router para que redireccione los puertos 80 y 443 al server sobre el que vamos a ejecutar este repositorio.
```

Tener en cuenta que la primera ejecución de init-letsencrypt.sh es posible que falle, bug de docker con los cp de los archivos. Repetir una segunda vez, y debería funcionar.

## Comandos utiles
```
docker volume rm nginx_data nginx_log nginx_www
docker volume create nginx_log
docker volume create nginx_data
docker volume create nginx_www

docker network rm nginx_network
docker network create nginx_network
```
