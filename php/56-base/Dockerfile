FROM php:5-apache

MAINTAINER Romain THERRAT <romain@pockost.com>

RUN a2enmod rewrite \
    && apt-get update && apt-get install -y \
        libcurl4-gnutls-dev zlib1g-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && docker-php-ext-configure opcache \
    && docker-php-ext-install opcache \
    && docker-php-ext-install mysqli curl zip pdo_mysql mbstring opcache

# GD installation only work when on his own RUN ????
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd
