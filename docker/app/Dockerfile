FROM php:8.0-fpm

EXPOSE 5173

ENV TZ Asia/Tokyo

RUN apt-get update && \
    apt-get install -y git unzip libzip-dev libicu-dev libonig-dev && \
    docker-php-ext-install intl pdo_mysql zip bcmath

RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get update && apt-get install -y nodejs

COPY ./docker/app/php.ini /usr/local/etc/php/php.ini

COPY --from=composer:2.2.4 /usr/bin/composer /usr/bin/composer

WORKDIR /app