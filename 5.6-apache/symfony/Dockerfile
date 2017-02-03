FROM php:5.6-apache
RUN \
    apt-get update && \
    apt-get install crudini libldap2-dev -y && \
    rm -rf /var/lib/apt/lists/* && \
    docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ && \
    docker-php-ext-install ldap && \
    docker-php-ext-install pdo pdo_mysql && \
    a2enmod rewrite 

# Install GD
RUN apt-get update && \
    apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install gd && rm -rf /var/lib/apt/lists/*

ENV PHP_INI_FILE /usr/local/etc/php/conf.d/php.ini
RUN touch $PHP_INI_FILE && \
    crudini --set $PHP_INI_FILE PHP error_log /proc/self/fd/2 && \
    crudini --set $PHP_INI_FILE PHP catch_workers_output yes && \
    crudini --set $PHP_INI_FILE Date date.timezone "Europe/Prague"

WORKDIR /var/www    
