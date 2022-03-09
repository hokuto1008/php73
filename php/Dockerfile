FROM php:7.3-apache

COPY ./php.ini /usr/local/etc/php/php.ini

RUN apt-get update && apt-get install -y vim zip unzip libonig-dev && \
docker-php-ext-install pdo_mysql

# node
RUN apt-get install -y nodejs npm && npm install n -g && n 14.17.3

# composer
COPY --from=composer /usr/bin/composer /usr/bin/composer

# xdebug
RUN pecl install xdebug && docker-php-ext-enable xdebug

# Laravel
#COPY httpd-base.conf /etc/apache2/sites-available/laravel.conf
#RUN a2dissite 000-default.conf && a2ensite laravel.conf && a2enmod rewrite

WORKDIR /var/www/html