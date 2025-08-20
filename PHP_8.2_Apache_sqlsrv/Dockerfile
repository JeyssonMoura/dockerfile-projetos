FROM php:8.2-apache

# Instalar dependências do sistema
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    gnupg2 \
    unixodbc \
    unixodbc-dev \
    libgssapi-krb5-2 \
    libssl-dev \
    libcurl4-openssl-dev \
    && rm -rf /var/lib/apt/lists/*

# Instalar extensões sqlsrv e pdo_sqlsrv via PECL
RUN pecl install sqlsrv pdo_sqlsrv \
    && docker-php-ext-enable sqlsrv pdo_sqlsrv

RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    && docker-php-ext-install mysqli pdo pdo_mysql curl \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Habilitar módulos do Apache (se precisar reescrita de URL)
RUN a2enmod rewrite

# Definir diretório de trabalho
WORKDIR /var/www/html

# Copiar os arquivos da aplicação para dentro do container
COPY . .

EXPOSE 80

# Permissões
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 755 /var/www/html