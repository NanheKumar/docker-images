FROM php:7.0-fpm

## Systme dependency
RUN apt-get update && \
    apt-get install -y libcurl4-openssl-dev \
	zlib1g-dev \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libpng-dev \
	libmcrypt-dev \
	libxml2-dev \
	libhiredis-dev 



#application dependency

RUN docker-php-ext-install curl && \
    docker-php-ext-install zip  && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install gd && \
    docker-php-ext-install mcrypt && \
    docker-php-ext-install xml && \
    docker-php-ext-install mbstring && \
    docker-php-ext-install mysqli && \
    pecl install -o -f redis && \
    docker-php-ext-enable redis

COPY ./php.ini /usr/local/etc/php/

WORKDIR /var/www/html
