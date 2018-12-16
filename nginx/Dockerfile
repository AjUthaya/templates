# Base image
FROM nginx:1.14.2-alpine

# Update/Upgrade APK
RUN apk update \
    upgrade \
    # Add bash
    & apk add bash \
    bash-doc \
    bash-completion