FROM yiisoftware/yii2-php:7.4-apache

WORKDIR /var/www/html
COPY products/ .

ENV PHP_MEMORY_LIMIT=512M
# Installing dependencies for the PHP modules
RUN apt-get update && apt-get install -y zip libzip-dev libpng-dev libicu-dev libonig-dev libcurl4-gnutls-dev libxml2-dev libfreetype6-dev

# Installing additional PHP modules
RUN docker-php-ext-install mysqli pdo pdo_mysql gd zip bcmath ctype intl mbstring opcache xml dom curl
#RUN a2enmod rewrite

RUN echo 'memory_limit = 2048M' >> /usr/local/etc/php/conf.d/docker-php-memlimit.ini;
RUN echo '\nerror_reporting=E_ERROR' >> /usr/local/etc/php/conf.d/base.ini;
RUN echo '\ndisplay_errors=On' >> /usr/local/etc/php/conf.d/base.ini;
RUN echo '\nshort_open_tag=On' >> /usr/local/etc/php/conf.d/base.ini;

RUN composer install -o
