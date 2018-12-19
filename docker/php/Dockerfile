# Base image
FROM php:7.0-fpm

# Add MySQL interfaces
RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable pdo_mysql

# Copy config files for php
COPY php.ini-development /usr/local/etc/php/php.ini-development
COPY php.ini-production /usr/local/etc/php/php.ini-production