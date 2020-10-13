FROM php:7.1.9-fpm

ADD sources.list    /etc/apt/sources.list

# 安装modules
RUN apt-get update && apt-get install -y --no-install-recommends \
        libicu-dev \
        libmemcached-dev \
        libz-dev \
        libpq-dev \
        libjpeg-dev \
        libpng-dev \
        libfreetype6-dev \
        libssl-dev \
        libmcrypt-dev \
        libxml2-dev \
        libbz2-dev \
        libjpeg62-turbo-dev \
        && docker-php-ext-configure gd \
                --enable-gd-native-ttf \
                --with-jpeg-dir=/usr/lib \
                --with-freetype-dir=/usr/include/freetype2 && \
                docker-php-ext-install gd \
        && docker-php-ext-install -j$(nproc) iconv mcrypt \
        && docker-php-ext-install mysqli \
        && docker-php-ext-install opcache \
        && pecl install redis \
        && docker-php-ext-enable redis \
        && docker-php-ext-install zip \
        && docker-php-ext-install pdo_mysql \
        && docker-php-ext-install xml \
        && apt-get clean \
        && php -r"copy('https://install.phpcomposer.com/installer','composer-setup.php');" \
        && php composer-setup.php --install-dir=/usr/bin --filename=composer \
        && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ \
        && usermod -u 1000 www-data


ADD php.ini    /usr/local/etc/php/php.ini
ADD php-fpm.d/www.conf    /usr/local/etc/php-fpm.d/www.conf


WORKDIR /opt

EXPOSE 9000