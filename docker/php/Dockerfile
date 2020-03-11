FROM php:7.4-fpm-alpine
LABEL maintainer "yoshis2"

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV TIME_ZONE Asia/Tokyo

RUN set -eux && \
  apk add --update-cache --no-cache --virtual=.build-dependencies tzdata && \
  cp /usr/share/zoneinfo/${TIME_ZONE} /etc/localtime && apk del .build-dependencies

# PHPプラグイン インストール
RUN docker-php-ext-install bcmath pdo_mysql

# composer インストール
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
  composer config -g repos.packagist composer https://packagist.jp