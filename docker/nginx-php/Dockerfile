# Base image
FROM php:7.2-fpm

# Add MySQL interfaces
RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable pdo_mysql

RUN apt-get -y install curl

# Update apt-get
# Install nginx
# Install git
# Clear out the local repository of retrieved package files
RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
    nginx \
    git \
    supervisor \
    procps \
    nano \
    build-essential \
    libssl-dev \
    zlib1g-dev \
    libpng-dev \
    && apt-get clean

# Copy config files for php
COPY php.ini-development /usr/local/etc/php/php.ini-development
COPY php.ini-production /usr/local/etc/php/php.ini-production

# Add PHP mbstring
RUN docker-php-ext-install mbstring

# Add PHP zip
RUN docker-php-ext-install zip

# Add PHP gd
RUN docker-php-ext-install gd

# Copy nginx config
COPY nginx.conf /etc/nginx/nginx.conf
COPY default.conf /etc/nginx/sites-available/default
COPY default.conf /etc/nginx/conf.d/default.conf

# Config to start nginx and php-fpm
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Set work directory
WORKDIR /usr/share/nginx/html

# Update ownership
RUN chown -R www-data:www-data /usr/share/nginx/html

# Start services
CMD ["/usr/bin/supervisord"]

# Expose nginx port
EXPOSE 80