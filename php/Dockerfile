FROM php:7.2.12-fpm

# install composer
RUN cd /usr/bin \
&& curl -s http://getcomposer.org/installer | php \
&& mv /usr/bin/composer.phar /usr/bin/composer

# apt-get
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim \
libpq-dev \
libfreetype6-dev \
libjpeg62-turbo-dev \
libpng-dev \
libxml2-dev \
libmemcached-dev \
zlib1g-dev

# use postgresql
RUN docker-php-ext-install pdo pdo_pgsql pgsql zip opcache soap bcmath \
&& docker-php-ext-install -j$(nproc) iconv \
&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
&& docker-php-ext-install -j$(nproc) gd

WORKDIR /var/www