FROM php:7.4-fpm

RUN apt-get update && apt-get install -y git zip unzip

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /app

COPY . ./

RUN --mount=type=ssh (mkdir -p -m 0600 ~/.ssh && ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts) \
   && composer install --prefer-dist --no-interaction --no-scripts
