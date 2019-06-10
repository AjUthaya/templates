# Base image
FROM php:7.2-fpm

# Add MySQL interfaces
RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable pdo_mysql

RUN apt-get -y install curl

# install the PHP extensions we need (https://make.wordpress.org/hosting/handbook/handbook/server-environment/#php-extensions)
RUN set -ex; \
    \
    savedAptMark="$(apt-mark showmanual)"; \
    \
    apt-get update; \
    apt-get install -y --no-install-recommends \
    libjpeg-dev \
    libmagickwand-dev \
    libpng-dev \
    ; \
    \
    docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; \
    docker-php-ext-install \
    bcmath \
    exif \
    gd \
    mysqli \
    zip \
    ; \
    pecl install imagick-3.4.4; \
    docker-php-ext-enable imagick; \
    \
    # reset apt-mark's "manual" list so that "purge --auto-remove" will remove all build dependencies
    apt-mark auto '.*' > /dev/null; \
    apt-mark manual $savedAptMark; \
    ldd "$(php -r 'echo ini_get("extension_dir");')"/*.so \
    | awk '/=>/ { print $3 }' \
    | sort -u \
    | xargs -r dpkg-query -S \
    | cut -d: -f1 \
    | sort -u \
    | xargs -rt apt-mark manual; \
    \
    apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false; \
    rm -rf /var/lib/apt/lists/*

# https://codex.wordpress.org/Editing_wp-config.php#Configure_Error_Logging
RUN { \
    echo 'error_reporting = 4339'; \
    echo 'display_errors = Off'; \
    echo 'display_startup_errors = Off'; \
    echo 'log_errors = On'; \
    echo 'error_log = /dev/stderr'; \
    echo 'log_errors_max_len = 1024'; \
    echo 'ignore_repeated_errors = On'; \
    echo 'ignore_repeated_source = Off'; \
    echo 'html_errors = Off'; \
    } > /usr/local/etc/php/conf.d/error-logging.ini

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