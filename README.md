Docker Workshop: Basics
=======================

Note: install [kitematic][kitematic] on mac to have docker running inside a VM.

## Images

- build the image within the image folder `docker build -t <tag-name> .`

### nginx

`nginx` exposed the port `80`.
Run `/usr/sbin/nginx -c /etc/nginx/nginx.conf` as the entrypoint.

Virtual host configuration can be mounted into `/etc/nginx/conf.d/`

### php-fpm

`php-fpm` exposed on the port `9000`.
Run `/usr/sbin/php5-fpm --nodaemonize` as the entrypoint.

## Containers

- start a container: `docker run [-it] [-d] [--rm] [-p <host-port>:<container-port>] [-v <host-volume:container-volume>] [-l <container-name>:<var-name>] --name <container-name> <tag-name> [cmd]`
- run a command on a running container `docker exec <container-name> <cmd>`
- start nginx linked with php-fpm (in `app` folder):    
  ```
  docker run -d --name php-fpm -v $(pwd)/html:/var/www/html demo/php-fpm:latest
  docker run -d --name nginx-php -v $(pwd)/config:/etc/nginx/conf.d -p 80:80 --link php-fpm:php  demo/nginx:latest
  ```
- start nginx linked with php-fpm with `docker-compose` (in `app` folder): `docker-compose up php`    



[kitematic]: https://kitematic.com/
