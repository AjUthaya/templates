# Base image
FROM node:10.14.2-alpine

# APK: Remove cache and tmp files
RUN rm -rf /var/cache/apk/* && \
    rm -rf /tmp/*

# APK: Update & Upgrade
RUN apk update \
    upgrade

# APK: Add Curl & Bash
RUN apk add curl bash

# Curl: Install nvm files & setup bash config
RUN curl --silent -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash 

# NVM: Create bash profile
RUN touch /root/.bashrc \ 
    & echo "source /root/.nvm/nvm.sh" >> /root/.bashrc

# NVM: Source bash profile 
RUN source /root/.bashrc