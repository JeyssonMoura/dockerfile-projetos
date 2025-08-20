FROM php:7.4-apache

# Habilitar mod_rewrite para permitir uso de .htaccess
RUN a2enmod rewrite

RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    && docker-php-ext-install mysqli pdo pdo_mysql curl \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Instalar dependências necessárias para a extensão GD
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd \
        --with-freetype \
        --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html

COPY . .

EXPOSE 80

RUN chown -R www-data:www-data /var/www