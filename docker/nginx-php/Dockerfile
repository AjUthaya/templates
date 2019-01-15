# Base image
FROM php:7.0-fpm

# Add MySQL interfaces
RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable pdo_mysql

# Update apt-get
# Install nginx
# Install git
# Clear out the local repository of retrieved package files
RUN apt-get update && apt-get install -y \
    nginx \
    git \
    && apt-get clean

# Copy config files for php
COPY php.ini-development /usr/local/etc/php/php.ini-development
COPY php.ini-production /usr/local/etc/php/php.ini-production

# Copy nginx config
COPY default.conf /etc/nginx/conf.d/default.conf

# Expose nginx port
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]