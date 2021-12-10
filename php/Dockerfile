FROM php:8.1-fpm

RUN sed -i "s@http://deb.debian.org@http://mirrors.aliyun.com@g" /etc/apt/sources.list

ARG TZ

RUN apt-get update && apt-get install -y \
        libzip-dev \
        zip \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) bcmath \
    && docker-php-ext-install -j$(nproc) zip \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) pdo pdo_mysql \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ \
    && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
    && apt-get -y autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /www
