FROM webdevops/apache:ubuntu-16.04

LABEL maintainer="Eric Pfeiffer <computerfr33k@users.noreply.github.com>"

ARG PHP_UPSTREAM_CONTAINER=php-fpm
ARG PHP_UPSTREAM_PORT=9000
ARG PHP_UPSTREAM_TIMEOUT=60
ARG DOCUMENT_ROOT=/var/www/

ENV WEB_PHP_SOCKET=${PHP_UPSTREAM_CONTAINER}:${PHP_UPSTREAM_PORT}

ENV WEB_DOCUMENT_ROOT=${DOCUMENT_ROOT}

ENV WEB_PHP_TIMEOUT=${PHP_UPSTREAM_TIMEOUT}

EXPOSE 80 443

WORKDIR /var/www/

COPY vhost.conf /etc/apache2/sites-enabled/vhost.conf
# had to add this..
#COPY sites/gripp.conf /etc/apache2/sites-enabled/
#COPY sites/api.gripp.conf /etc/apache2/sites-enabled/
#COPY ${APACHE_SITES_PATH}/api.gripp.conf /etc/apache2/sites-enabled/
#COPY ${APACHE_SITES_PATH}/gripp.conf /etc/apache2/sites-enabled/

ENTRYPOINT ["/opt/docker/bin/entrypoint.sh"]

CMD ["supervisord"]
