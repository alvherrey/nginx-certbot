# nginx-poc
nginx server PoC using docker


## Prerequisitos
docker volume rm nginx_data nginx_log nginx_www
docker volume create nginx_log
docker volume create nginx_data
docker volume create nginx_www

docker network rm nginx_network
docker network create nginx_network
