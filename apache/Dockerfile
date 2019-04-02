ARG APACHE_VERSION=""
ARG TIMEZONE="Asia/Ho_Chi_Minh"
FROM httpd:${APACHE_VERSION:+${APACHE_VERSION}-}alpine

ENV TZ ${TIMEZONE:-Asia/Ho_Chi_Minh}

RUN apk update; \
    apk upgrade; \
    apk add tzdata;

RUN ln -snf /usr/share/zoneinfo/${TZ} /etc/localtime && echo ${TZ} > /etc/timezone

# Copy apache vhost file to proxy php requests to php-fpm container
COPY demo.apache.conf /usr/local/apache2/conf/demo.apache.conf
RUN echo "Include /usr/local/apache2/conf/demo.apache.conf" \
    >> /usr/local/apache2/conf/httpd.conf
