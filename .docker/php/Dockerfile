FROM php:7.4-fpm

ENV XDEBUG_VERSION=2.9.4

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
        git \
        zip \
        unzip

RUN pecl install xdebug-${XDEBUG_VERSION} && \
    docker-php-ext-enable xdebug

RUN docker-php-ext-install \
    pdo \
    pdo_mysql

RUN php -r "readfile('http://getcomposer.org/installer');" | \
    php -- --install-dir=/usr/local/bin/ --filename=composer

RUN curl -LsS https://cs.sensiolabs.org/download/php-cs-fixer-v2.phar -o /usr/local/bin/php-cs-fixer && \
    chmod a+x /usr/local/bin/php-cs-fixer

RUN curl -LsS https://get.sensiolabs.org/security-checker.phar -o /usr/local/bin/security-checker && \
    chmod a+x /usr/local/bin/security-checker

RUN curl -LsS https://get.symfony.com/cli/installer -o symfony-installer && \
    chmod a+x ./symfony-installer && \
    ./symfony-installer --install-dir=/usr/local/bin && \
    rm ./symfony-installer && \
    chmod a+x /usr/local/bin/symfony
