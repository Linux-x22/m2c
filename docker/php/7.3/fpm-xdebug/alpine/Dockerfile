FROM        alpine:3.11

LABEL       maintainer="Mage2click, Dmitry Shkoliar @shkoliar"

ENV         UID=1000
ENV         GID=1000

COPY        conf/php.ini /etc/php7/conf.d/
COPY        conf/php-fpm.d/zz-docker.conf /etc/php7/php-fpm.d/
COPY        bin/docker-entrypoint /php-fpm
COPY        bin/prompt /etc/profile.d/prompt.sh

RUN         apk update && \
            apk add --no-cache \
                php7 \
                php7-bcmath \
                php7-calendar \
                php7-ctype \
                php7-curl \
                php7-dom \
                php7-fileinfo \
                php7-fpm \
                php7-gd \
                php7-gettext \
                php7-iconv \
                php7-intl \
                php7-json \
                php7-mbstring \
                php7-mysqli \
                php7-opcache \
                php7-openssl \
                php7-phar \
                php7-pdo_mysql \
                php7-simplexml \
                php7-soap \
                php7-sockets \
                php7-sodium \
                php7-tokenizer \
                php7-xml \
                php7-xmlwriter \
                php7-xsl \
                php7-zip \
                php7-pecl-amqp \
                php7-pecl-igbinary \
                php7-pecl-mcrypt \
                php7-pecl-redis \
                php7-pecl-ssh2 \
                php7-pecl-xdebug \
                curl \
                bash \
                busybox-suid \
                gnupg \
                gzip \
                htop \
                openssh \
                lsof && \
            \
            \
            sed -i -e 's/^;zend_extension/\zend_extension/g' /etc/php7/conf.d/xdebug.ini && \
            \
            \
            rm -rf /var/cache/apk/* && \
            rm -rf /tmp/* && \
            \
            \
            addgroup -g 1000 -S app && \
            adduser -u 1000 -S app -G app -h /var/www -s /bin/bash && \
            \
            \
            mkdir -p /var/www/html /var/www/.config /var/www/.npm /sock && \
            \
            \
            ln -sf /usr/sbin/php-fpm7 /usr/sbin/php-fpm && \
            ln -sf /etc/init.d/php-fpm7 /etc/init.d/php-fpm && \
            \
            \
            chmod +x /php-fpm

ENTRYPOINT  /php-fpm

WORKDIR     /var/www/html