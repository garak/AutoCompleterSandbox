FROM php:7.1-cli

MAINTAINER Massimiliano Arione <garakkio@gmail.com>

ARG HOST_UID

# Add git and unzip
RUN apt-get update && apt-get install -y git unzip

# Set timezone
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Rome /etc/localtime
RUN "date"

# Install extensions
RUN apt-get install -y zlib1g-dev libicu-dev g++ vim mysql-client netcat-openbsd
RUN docker-php-ext-install pdo pdo_mysql intl 
RUN docker-php-ext-configure intl

RUN echo "memory_limit = 1024M" >> /usr/local/etc/php/conf.d/memory-limit.ini

# Configure user
RUN mkdir /user
RUN useradd -u $HOST_UID -d /user -s /bin/bash user
RUN chown user /user
USER user

WORKDIR /user/sandbox
