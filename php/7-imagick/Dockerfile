FROM pockost/base-php:7

RUN apt-get update && apt-get install -y \
        libicu-dev \
        libxslt1-dev \
        libmagickwand-dev \
        imagemagick \
    && docker-php-ext-install intl xsl exif \
    && pecl install imagick \
    && echo "extension=imagick.so" > /usr/local/etc/php/conf.d/imagick.ini
