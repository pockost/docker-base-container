FROM php:7.1.26-apache

RUN a2enmod rewrite \
    && apt-get update \
    && apt-get install -y \
       git \
       unzip \
       libmcrypt-dev \
       libjpeg62-turbo-dev \
       libpng-dev \
       libfreetype6-dev \
       libbz2-dev \
       libxslt1-dev \
       libmagickwand-dev \
    && curl -sS -o /tmp/icu.tar.gz -L http://download.icu-project.org/files/icu4c/63.1/icu4c-63_1-src.tgz \
    && tar -zxf /tmp/icu.tar.gz -C /tmp \
    && cd /tmp/icu/source \
    && ./configure --prefix=/usr/local \
    && make && make install \
    && pecl install redis apcu xdebug imagick \
    && docker-php-ext-configure intl --with-icu-dir=/usr/local \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && docker-php-ext-install intl gd pdo_mysql mysqli mcrypt zip calendar bcmath bz2 xsl exif opcache \
    && docker-php-ext-enable redis apcu xdebug imagick \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/icu*
