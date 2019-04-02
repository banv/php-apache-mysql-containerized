ARG PHP_VERSION=""
FROM php:${PHP_VERSION:+${PHP_VERSION}-}fpm-alpine

ARG TIMEZONE="Asia/Ho_Chi_Minh"
ENV TZ ${TIMEZONE}

RUN apk update; \
    apk upgrade; \
    apk add tzdata;

RUN ln -snf /usr/share/zoneinfo/${TZ} /etc/localtime && echo ${TZ} > /etc/timezone

RUN docker-php-ext-install mysqli
RUN printf "[PHP]\ndate.timezone = ${TZ}\n" > /usr/local/etc/php/conf.d/tzone.ini
