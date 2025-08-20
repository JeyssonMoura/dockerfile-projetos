# Dockerfile para projetos em PHP

## Versões disponíveis

### PHP 7.4 Apache

    Extensões:
        - mysqli
        - pdo
        - pdo_mysql
        - curl
        - gd

#### Comandos

```docker
# Imagem
docker build -t php-7-4-apache .

# Container com Volume
docker run -d -p 3001:80 --name php-7-4-apache-container -v LOCAL_DO_PROJETO:/var/www/html --rm php-7-4-apache
```

### PHP 8.0 Apache

    Extensões:
        - mysqli
        - pdo
        - pdo_mysql
        - curl
        - gd

#### Comandos

```docker
# Imagem
docker build -t php-8-0-apache .

# Container com Volume
docker run -d -p 3002:80 --name php-8-0-apache-container -v LOCAL_DO_PROJETO:/var/www/html --rm php-8-0-apache
```

### PHP 8.2 Apache

    Extensões:
        - mysqli
        - pdo
        - pdo_mysql
        - curl
        - gd
        - sqlsrv
        - pdo_sqlsrv

#### Comandos

```docker
# Imagem
docker build -t php-8-2-apache .

# Container com Volume
docker run -d -p 3003:80 --name php-8-2-apache-container -v LOCAL_DO_PROJETO:/var/www/html --rm php-8-2-apache
```
