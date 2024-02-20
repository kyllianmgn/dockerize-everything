# Créer un Dockerfile pour cette application en mode production

FROM php:8.3-fpm

LABEL maintainer="Gilles Kounkoud <gkounkoud@myges.com>"
LABEL version="1.0"

#Dépendances
RUN apt-get update && apt-get install -y \
        libicu-dev \
        wget \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

#Installation de intl
RUN docker-php-ext-install intl

# Installation de composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Configuration de l'application
WORKDIR /var/www

COPY . .

RUN composer install --no-dev --optimize-autoloader

RUN php bin/console asset-map:compile

RUN chown -R www-data:www-data /var/www/html/

USER www-data
