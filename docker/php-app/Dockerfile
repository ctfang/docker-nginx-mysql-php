FROM php:7.1-fpm

# 基础扩扩展
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev vim \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
    && docker-php-ext-install gd pdo_mysql zip opcache

ADD ./composer.phar /usr/local/bin/composer

# swoole按照
COPY ./php7-ini/20-swoole.ini /usr/local/etc/php/conf.d/20-swoole.ini
COPY ./php7-ext/swoole.so /usr/local/lib/php/extensions/no-debug-non-zts-20160303/swoole.so

# phalcon安装
COPY ./php7-ini/20-phalcon.ini /usr/local/etc/php/conf.d/20-phalcon.ini
COPY ./php7-ext/phalcon-v3.2.1.so /usr/local/lib/php/extensions/no-debug-non-zts-20160303/phalcon-v3.2.1.so