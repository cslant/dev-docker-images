FROM node:22.12.0-alpine
LABEL maintainer="Tan Nguyen <tannp@cslant.com>"
LABEL authors="cslant"
LABEL description="Node.js 22 image for CSlant development"

ARG USER_ID=1000
ARG GROUP_ID=1000

## Set Environment
ENV USER_ID=$USER_ID
ENV GROUP_ID=$GROUP_ID

RUN apk add --no-cache \
    git \
    xdg-utils

RUN deluser node

## Add user
RUN addgroup -g ${USER_ID} csdev; \
    adduser -D -u ${USER_ID} -G csdev csdev

## Enable Yarn 4
RUN corepack enable

USER csdev

RUN echo Y | yarn -v
RUN corepack prepare yarn@4.8.1 --activate

## Install Sass (use npm since Yarn 4 doesn't support global add)
RUN npm install -g sass

WORKDIR /var/dev

CMD ["ash", "-l"]
