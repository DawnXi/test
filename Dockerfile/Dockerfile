FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

#安装 nginx php7-fpm 等软件  php7-dev 是要安装的，装扩展就依赖它的phpize，php-config
RUN apt-get update && apt-get install -yq --no-install-recommends \
    apt-utils \
    curl \
    # Install nginx
    nginx \
    # Install php 7.2
    php7.2 \
    php7.2-cli \
    php7.2-json \
    php7.2-curl \
    php7.2-fpm \
    php7.2-gd \
    php7.2-ldap \
    php7.2-mbstring \
    php7.2-mysql \
    php7.2-soap \
    php7.2-sqlite3 \
    php7.2-xml \
    php7.2-zip \
    php7.2-intl \
    php-imagick \
    # Install tools
    openssl \
    nano \
    graphicsmagick \
    imagemagick \
    ghostscript \
    mysql-client \
    iputils-ping \
    locales \
    sqlite3 \
    ca-certificates \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

#安装 composer 
RUN curl -sS https://getcomposer.org/installer \
        | php -- --install-dir=/usr/local/bin --filename=composer

#更新nginx 配置文件信息
#ADD nginx_nginx.conf /etc/nginx/nginx.conf
ADD nginx_default.conf /etc/nginx/sites-available/default

#写入phpinfo.php 配置文件
RUN mkdir -p /public && echo "<?php phpinfo(); ?>" > ${APP_DIR}/phpinfo.php
#RUN chmod 0777 /public/web

#暴露端口 80 443
EXPOSE 80 443