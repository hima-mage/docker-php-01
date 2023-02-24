FROM php:8.1-fpm-alpine

RUN docker-php-ext-install pdo pdo_mysql

# allow super use
ENV COMPOSER_ALLOW_SUPERUSER=1

# obtain composer
COPY --from=composer:2.4 /usr/bin/composer /usr/bin/composer

# copy composer.json , composer.lock
COPY ./app/composer.* ./

# install
RUN composer install --prefer-dist --no-dev --no-scripts --no-progress --no-interaction

# copy application files to working directory
COPY ./app .

# run composer dump-autoload --optimize
RUN composer dump-autoload --optimize