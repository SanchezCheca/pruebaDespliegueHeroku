FROM php:7.4.15-apache

COPY ./apache/000-default.conf /etc/apache2/sites-available/

COPY . /var/www/html

RUN docker-php-ext-install pdo pdo_mysql \
    && apt update \
    && apt-get update \
    && apt-get install -y zip \
    && apt-get install -y unzip \
    && set -eux \
    && apt-get install -y libzip-dev zlib1g-dev \
    && docker-php-ext-install zip \
    && a2enmod rewrite \
    && service apache2 restart \
    && apt-get clean

EXPOSE 80