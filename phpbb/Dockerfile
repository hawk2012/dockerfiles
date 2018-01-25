#
# Dockerfile for phpBB
#

FROM php:7-apache
MAINTAINER kev <noreply@easypi.pro>

RUN a2enmod rewrite

RUN set -xe \
    && apt-get update \
    && apt-get install -y curl unzip zip bzip2 libpq-dev libpng12-dev libjpeg-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
    && docker-php-ext-install gd mysqli pgsql

WORKDIR /var/www/html

ENV PHPBB_VERSION 2.0.4
ENV PHPBB_URL https://bitbucket.org/Sumanai/phpbbex-2.0/downloads/phpbbex-${PHPBB_VERSION}.zip
ENV PHPBB_FILE phpbbex.zip

RUN set -xe \
    && curl -fSL ${PHPBB_URL} -o ${PHPBB_FILE} \
    && unzip ${PHPBB_FILE} \
    && rm ${PHPBB_FILE} \
    && chown -R www-data:www-data .

