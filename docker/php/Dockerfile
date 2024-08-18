FROM php:8.2-fpm

RUN apt-get update && \
    apt-get install -y --no-install-recommends ssmtp vim curl debconf subversion git apt-transport-https apt-utils \
    build-essential locales acl mailutils wget zip unzip gnupg gnupg1 gnupg2 zlib1g-dev libicu-dev g++

RUN apt-get install -y libzip-dev zlib1g-dev libpng-dev && \
    docker-php-ext-install zip
    
RUN docker-php-ext-configure intl && \
    docker-php-ext-install intl pdo_mysql

RUN docker-php-ext-install gd bcmath opcache

RUN pecl install xdebug-3.2.2 \
    && docker-php-ext-enable xdebug \
    && echo "xdebug.mode=develop,debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.client_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.start_with_request=trigger" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
    
RUN pecl install apcu && docker-php-ext-enable apcu

RUN export COMPOSER_HOME=/usr/local/composer && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer