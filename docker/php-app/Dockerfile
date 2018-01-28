FROM php:7.1-fpm

# 基础扩扩展
RUN docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql

# swoole按照
COPY ./php7-ini/20-swoole.ini /usr/local/etc/php/conf.d/20-swoole.ini
COPY ./php7-ext/swoole.so /usr/local/lib/php/extensions/no-debug-non-zts-20160303/swoole.so

# phalcon安装
COPY ./php7-ini/20-phalcon.ini /usr/local/etc/php/conf.d/20-phalcon.ini
COPY ./php7-ext/phalcon-v3.2.1.so /usr/local/lib/php/extensions/no-debug-non-zts-20160303/phalcon-v3.2.1.so