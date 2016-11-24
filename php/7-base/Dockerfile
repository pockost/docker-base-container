FROM php:7-apache

MAINTAINER Romain THERRAT <romain@pockost.com>

RUN a2enmod rewrite \
    && apt-get update && apt-get install -y \
        libcurl4-gnutls-dev git zlib1g-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        jpegoptim \
    && git clone -b php7 https://github.com/phpredis/phpredis.git /usr/src/php/ext/redis \
    && docker-php-ext-install iconv mcrypt redis \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && docker-php-ext-install mysqli curl zip pdo_mysql gd mbstring \
    && docker-php-ext-configure opcache \
    && docker-php-ext-install opcache
