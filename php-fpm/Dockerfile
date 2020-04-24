######
# See: https://hub.docker.com/_/php/
######

FROM php:7.0-fpm
LABEL maintainer="Yu-Hsiang Huang <yhhuang79@gmail.com>"

######
# You can install php extensions using docker-php-ext-install
######

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install opcache \
    && docker-php-ext-install fileinfo \
    && pecl install redis-5.1.1 \
    && docker-php-ext-enable redis
