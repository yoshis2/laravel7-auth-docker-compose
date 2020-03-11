FROM php:7.4-fpm-alpine
LABEL maintainer "yoshis2"

ENV TIME_ZONE Asia/Tokyo

RUN set -eux && \
  apk add --update-cache --no-cache --virtual=.build-dependencies tzdata && \
  cp /usr/share/zoneinfo/${TIME_ZONE} /etc/localtime

# PHPプラグイン インストール
RUN apk update && apk add git && docker-php-source extract && \
  git clone -b 5.2.0 --depth 1 https://github.com/phpredis/phpredis.git /usr/src/php/ext/redis && \
  docker-php-ext-install bcmath pdo_mysql redis

# composer インストール
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
  composer config -g repos.packagist composer https://packagist.jp