FROM debian:latest

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -y update
RUN apt-get -y install php5-fpm

ADD config/php-fpm.conf /etc/php5/fpm/php-fpm.conf
ADD config/www.conf /etc/php5/fpm/pool.d/www.conf

RUN mkdir -p /var/www/html

EXPOSE 9000
ENTRYPOINT ["/usr/sbin/php5-fpm", "--nodaemonize"]
