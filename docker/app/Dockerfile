FROM php:8.1-fpm

WORKDIR /var/www
    
RUN rm /etc/apt/preferences.d/no-debian-php

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        zlib1g-dev \
        libxml2-dev \
        libzip-dev \
        ffmpeg \
        libonig-dev \
        cron \
        vim \
        graphviz \
        libssl-dev \
        supervisor \
        libxrender1 \
        fontconfig \
        libxtst6 \
        xz-utils \
        php-soap \
        iputils-ping\
    && docker-php-ext-configure gd \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install zip \
    && docker-php-ext-install soap \
    && docker-php-source delete

RUN pecl install redis-5.3.3 && docker-php-ext-enable redis
RUN pecl install mongodb && docker-php-ext-enable mongodb

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

RUN chown -R www-data:www-data /var/www
RUN chmod -R 777 /var/www

USER www-data

EXPOSE 9000
CMD [ "php-fpm" ]
