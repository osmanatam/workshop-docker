FROM debian:latest

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -y update
RUN apt-get -y install nginx nginx-extras

ADD config/nginx.conf /etc/nginx/nginx.conf
ADD config/fastcgi_params /etc/nginx/fastcgi_params

EXPOSE 80
VOLUME ["/var/www/html"]
ENTRYPOINT ["/usr/sbin/nginx", "-c", "/etc/nginx/nginx.conf"]
