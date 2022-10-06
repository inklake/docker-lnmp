FROM php:7.3.1-fpm-alpine

LABEL maintainer="inklake@qq.com"

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN apk upgrade --update

# timezone
RUN apk add -U tzdata
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN apk del tzdata

# install comnposer
COPY src/composer.phar /usr/local/bin/composer
RUN composer config -g repo.packagist composer https://packagist.phpcomposer.com

# install php extend
RUN docker-php-ext-install -j$(nproc) pcntl exif fileinfo mysqli pdo_mysql bcmath

# install zip
RUN apk add libzip-dev
RUN docker-php-ext-install zip

# install gd
RUN apk add freetype-dev libjpeg-turbo-dev libpng-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# prepare pecl
RUN apk add g++ autoconf make
RUN pecl channel-update pecl.php.net

# install redis
RUN pecl install redis && docker-php-ext-enable redis

# over
WORKDIR /usr/share/nginx/html
