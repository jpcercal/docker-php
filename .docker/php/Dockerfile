FROM php:7-fpm

RUN apt-get update && apt-get install -y zlib1g-dev

RUN docker-php-ext-install \
    pdo \
    pdo_mysql \
    zip

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

RUN curl -L https://cs.sensiolabs.org/download/php-cs-fixer-v2.phar -o php-cs-fixer && chmod +x php-cs-fixer && mv php-cs-fixer /usr/local/bin/php-cs-fixer
