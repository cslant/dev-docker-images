ARG PHP_VERSION=8.5

FROM php:${PHP_VERSION}-fpm-alpine
LABEL maintainer="Tan Nguyen <tannp@cslant.com>"
LABEL authors="cslant"
LABEL description="PHP 8.5 image for CSlant development"

## Make php ini
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

## Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && mv composer.phar /usr/local/bin/composer

## Config user
ARG USER_ID=1000
ARG GROUP_ID=1000
ENV USER_ID=${USER_ID}
ENV GROUP_ID=${GROUP_ID}

# ensure www-data user exists
RUN set -eu; \
    addgroup -g ${USER_ID} csdev; \
    adduser -D -u ${USER_ID} -G csdev csdev

ADD cslant.php.ini "$PHP_INI_DIR/conf.d/cslant.ini"
ADD cslant.pool.conf /usr/local/etc/php-fpm.d/www.conf

# Default workdir
WORKDIR /var/dev

## Install system packages and Git
RUN apk add --no-cache git

## Install Ext
ADD --chmod=0755 https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN install-php-extensions soap pcntl bcmath gd exif sockets zip redis intl pdo_pgsql pgsql pdo_mysql mysqli curl fileinfo xml mbstring sodium bcmath

# Install WP-CLI
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar && \
    chmod +x wp-cli.phar && \
    mv wp-cli.phar /usr/local/bin/wp && \
    wp --allow-root cli version

# Create necessary directories and set permissions
RUN mkdir -p /home/csdev/.wp-cli/cache && \
    chown -R csdev:csdev /home/csdev/.wp-cli && \
    chmod 777 /home/csdev/.wp-cli/cache

# Create necessary directories for WP-CLI
RUN mkdir -p /home/csdev/.wp-cli/cache && \
    chown -R csdev:csdev /home/csdev/.wp-cli && \
    chmod 777 /home/csdev/.wp-cli/cache

# Switch to non-root user
USER csdev

# Set WP-CLI configuration
ENV WP_CLI_CACHE_DIR=/home/csdev/.wp-cli/cache

CMD ["php-fpm"]
