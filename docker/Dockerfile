ARG PHP_VERSION
FROM php:${PHP_VERSION} AS base

## Diretório da aplicação
ARG APP_DIR=/var/www/app

## Versão da Lib do Redis para PHP
ARG REDIS_LIB_VERSION=6.1.0

### apt-utils é um extensão de recursos do gerenciador de pacotes APT
RUN apt-get update -y && apt-get install -y --no-install-recommends \
    apt-utils \
    sudo \
    supervisor

# dependências recomendadas de desenvolvido para ambiente linux
RUN apt-get update && apt-get install -y \
    autoconf \
    libpng-dev \
    libpq-dev \
    libxml2-dev \
    libzip-dev \
    unzip \
    zlib1g-dev \
    sqlite3 \
    libsqlite3-dev 

RUN docker-php-ext-install pdo session xml

# habilita instalação do Redis
RUN pecl install redis-${REDIS_LIB_VERSION} \
    && docker-php-ext-enable redis 

RUN docker-php-ext-install zip iconv simplexml pcntl gd fileinfo pdo pgsql pdo_pgsql


# habilita instalação do xdebug
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# habilita instalação do opentelemetry
RUN pecl install opentelemetry \
    && docker-php-ext-enable opentelemetry

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY ./docker/supervisord/supervisord.conf /etc/supervisor/conf.d/supervisord.conf
# COPY ./docker/supervisord/vite.conf /etc/supervisor/conf.d/vite.conf

# COPY ./docker/supervisord/conf /etc/supervisord.d/
### Supervisor permite monitorar e controlar vários processos (LINUX)
### Bastante utilizado para manter processos em Daemon, ou seja, executando em segundo plano

COPY ./docker/php/extra-php.ini /usr/local/etc/php/conf.d/99_extra.ini
COPY ./docker/php/extra-php-fpm.conf /etc/php8/php-fpm.d/www.conf

RUN usermod -u 1000 www-data
RUN groupmod -g 1000 www-data

### Permite que o usuário www-data execute comandos como root
RUN echo "alias runaswww='sudo -u www-data'" >> ~/.bashrc

FROM base AS app

WORKDIR $APP_DIR
RUN cd $APP_DIR
RUN chown www-data:www-data $APP_DIR

COPY --chown=www-data:www-data ./app .
RUN rm -rf vendor
RUN composer install --no-interaction

# Instalação do Nginx
RUN apt-get install nginx -y
RUN rm -rf /etc/nginx/sites-enabled/* && rm -rf /etc/nginx/sites-available/*
COPY ./docker/nginx/sites.conf /etc/nginx/sites-enabled/default.conf
COPY ./docker/nginx/error.html /var/www/html/error.html

RUN apt-get clean && rm -rf /var/lib/apt/lists/* && \
    curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs
RUN apt update -y && apt install nano git -y

# USER www-data

# CMD ["sh", "-c", "npm run dev -- --host & /usr/bin/supervisord -c /etc/supervisor/supervisord.conf"]

CMD [ "/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]
