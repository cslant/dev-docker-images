ARG PHP_VERSION=8.4

FROM php:${PHP_VERSION}-cli-alpine
LABEL maintainer="Tan Nguyen <tannp@cslant.com>"
LABEL authors="cslant"
LABEL description="PHP Worker image for CSlant development"

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

ARG USER_ID=1000
ARG GROUP_ID=1000
ENV USER_ID ${USER_ID}
ENV GROUP_ID ${GROUP_ID}

RUN set -eu; \
    addgroup -g ${USER_ID} csdev; \
    adduser -D -u ${USER_ID} -G csdev csdev

ADD cslant.php.ini "$PHP_INI_DIR/conf.d/blog.ini"

WORKDIR /var/dev

ADD --chmod=0755 https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN install-php-extensions soap pcntl bcmath gd exif sockets zip xdebug redis intl pdo_pgsql pgsql pdo_mysql mysqli

## Install supervisord
RUN apk add --no-cache supervisor

ADD supervisord.conf /etc/supervisord.conf

CMD ["supervisord", "-c", "/etc/supervisord.conf", "-n"]
