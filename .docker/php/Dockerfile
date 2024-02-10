FROM php:8.2-fpm

ARG WWW_UID
ARG WWW_GID

COPY root /

RUN apt update && apt install -y mc nano git libfreetype6-dev libjpeg62-turbo-dev libpng-dev libzip-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install pdo_mysql mysqli zip gd

RUN groupadd -g $WWW_GID sail && \
    useradd -g sail -u $WWW_UID -s /bin/bash -m sail

COPY --from=composer:2.6 /usr/bin/composer /usr/bin/composer

WORKDIR /app
