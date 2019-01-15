# Base image
FROM php:7.2-fpm

# Add MySQL interfaces
RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable pdo_mysql

# Update apt-get
# Install nginx
# Install git
# Clear out the local repository of retrieved package files
RUN apt-get update && apt-get install -y \
    nginx \
    git \
    supervisor \
    procps \
    nano \
    && apt-get clean

# Copy config files for php
COPY php.ini-development /usr/local/etc/php/php.ini-development
COPY php.ini-production /usr/local/etc/php/php.ini-production

# Copy nginx config
COPY nginx.conf /etc/nginx/nginx.conf
COPY default.conf /etc/nginx/sites-available/default
COPY default.conf /etc/nginx/conf.d/default.conf

# Config to start nginx and php-fpm
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Set work directory
WORKDIR /usr/share/nginx/html

# Start services
CMD ["/usr/bin/supervisord"]

# Expose nginx port
EXPOSE 80