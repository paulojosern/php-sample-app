FROM php:7.2-apache
# local onde sera exposto
WORKDIR /var/www/html/
# COPY . /var/www/html/
COPY . .
# instalar extensão mysqli
RUN docker-php-ext-install mysqli
