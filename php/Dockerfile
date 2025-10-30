FROM php:8.2-fpm

RUN apt-get update && apt-get install -y --no-install-recommends \
    libicu-dev \
    libjpeg-dev \
    libpng-dev \
    libfreetype6-dev \
    libonig-dev \        
    zip unzip git \
    && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install -j"$(nproc)" pdo_mysql mbstring intl gd

RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
COPY php.ini /usr/local/etc/php/conf.d/php.ini
WORKDIR /var/www/html
