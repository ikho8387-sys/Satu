FROM php:8.4-fpm-alpine

RUN apk add --no-cache \
        bash \
        curl \
        freetype \
        libjpeg-turbo \
        libpng \
        libwebp \
        libzip \
        icu-libs \
        oniguruma \
        libxml2 \
    && apk add --no-cache --virtual .build-deps \
        $PHPIZE_DEPS \
        freetype-dev \
        libjpeg-turbo-dev \
        libpng-dev \
        libwebp-dev \
        libzip-dev \
        icu-dev \
        oniguruma-dev \
        libxml2-dev \
    && docker-php-ext-configure gd \
        --with-freetype \
        --with-jpeg \
        --with-webp \
    && docker-php-ext-install -j$(nproc) \
        bcmath \
        gd \
        intl \
        mbstring \
        mysqli \
        pdo_mysql \
        xml \
        zip \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/*

WORKDIR /var/www/html
