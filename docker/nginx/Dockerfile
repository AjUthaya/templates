# Base image
FROM nginx:1.15-alpine

# Add www-data
RUN addgroup -g 1000 -S www-data \
    && adduser -u 1000 -D -S -G www-data www-data

# Update/upgrade packages list
RUN apk update \
    upgrade \
    && apk add \
    # Bash
    bash \
    bash-doc \
    bash-completion \
    # Git
    git \
    # Nano
    nano \
    # Curl
    curl \
    && rm -f /var/cache/apk/*

# Copy nginx config
COPY nginx.conf /etc/nginx/nginx.conf
COPY default.conf /etc/nginx/sites-available/default
COPY default.conf /etc/nginx/conf.d/default.conf

# Set work directory
WORKDIR /usr/share/nginx/html

# Update ownership
RUN chown -R www-data:www-data /usr/share/nginx/html

# Start services
CMD ["nginx", "-g", "daemon off;"]

# Expose nginx port
EXPOSE 80