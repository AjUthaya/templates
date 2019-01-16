# Base image
FROM node:10.15-alpine

# Add www-data
RUN addgroup -g 2000 -S www-data \
    && adduser -u 2000 -D -S -G www-data www-data

# Update/upgrade packages list
RUN apk update \
    upgrade \
    && apk add \
    # Bash
    bash \
    bash-doc \
    bash-completion \
    # NGINX
    nginx \
    # Git
    git \
    # Nano
    nano \
    # Curl
    curl \
    && rm -f /var/cache/apk/*

# NVM
RUN curl --silent -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

# NVM: Create bash profile
RUN touch /root/.bashrc \
    & echo "source /root/.nvm/nvm.sh" >> /root/.bashrc

# NVM: Source bash profile
RUN source /root/.bashrc

# Copy nginx config
COPY nginx.conf /etc/nginx/nginx.conf
COPY default.conf /etc/nginx/sites-available/default
COPY default.conf /etc/nginx/conf.d/default.conf

# Set work directory
WORKDIR /usr/share/nginx/html

# Start services
CMD ["nginx", "-g", "daemon off;"]

# Expose nginx port
EXPOSE 80