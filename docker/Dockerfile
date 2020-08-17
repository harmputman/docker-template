FROM php:7.4-apache

RUN apt-get update && apt-get upgrade -y

RUN a2enmod rewrite

RUN docker-php-ext-install mysqli

# install composer
RUN curl --silent --show-error https://getcomposer.org/installer | php

WORKDIR /var/www/html

EXPOSE 80
