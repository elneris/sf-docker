FROM php:7.4-fpm
MAINTAINER Elneris Dang <elneris.dang@omnilog.fr>

# Update package, install rsync
RUN apt-get update \
    && apt-get install -y rsync

# Add xdebug apcu opcache
RUN pecl install xdebug apcu \
    && docker-php-ext-enable xdebug apcu \
    && docker-php-ext-install opcache

# Add Composer
RUN apt-get install -y git unzip \
    && curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer

# Add pdo_mysql or pdo_pgsql
#RUN docker-php-ext-install pdo_mysql
RUN apt-get install -y libpq-dev \
    && docker-php-ext-configure pdo_pgsql --with-pdo-pgsql=/var/lib/postgresql \
    && docker-php-ext-install pdo_pgsql

# Add intl
RUN apt-get install -y zlib1g-dev libicu-dev g++ \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

# Add zip
RUN apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    && docker-php-ext-install zip

# Php config
COPY php.ini /usr/local/etc/php/php.ini

# Create dev user for specified uid:gid
ARG USER_ID=1000
ARG GROUP_ID=1000

RUN groupadd devdocker -g ${GROUP_ID} \
    && useradd -m -u ${USER_ID} -g ${GROUP_ID} dev

USER dev
