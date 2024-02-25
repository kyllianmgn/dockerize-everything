# Créer un Dockerfile pour cette application en mode production

FROM php:8.3-fpm
#Dépendances
RUN apt-get update && apt-get install -y \
        libicu-dev \
        libzip-dev \
        zip \
        git\
    && docker-php-ext-install intl zip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

#Installation de intl
RUN docker-php-ext-install intl

# Installation de composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

#RUN mv composer.phar /usr/bin/composer

WORKDIR /var/www/html

COPY . .

ENV COMPOSER_ALLOW_SUPERUSER=1
# Configuration de l'application

RUN composer install --no-dev --optimize-autoloader

RUN php bin/console asset-map:compile

COPY --chown=www-data:www-data . .

USER www-data

CMD ["php-fpm"]


