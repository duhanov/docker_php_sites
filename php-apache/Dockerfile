FROM php:8.1-apache
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli && docker-php-ext-install pdo pdo_mysql  && docker-php-ext-enable pdo pdo_mysql
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y \
        libapache2-mod-rpaf \
        libzip-dev \
        zip \
        && docker-php-ext-install zip

RUN echo "LoadModule rpaf_module /usr/lib/apache2/modules/mod_rpaf.so" > /etc/apache2/mods-available/rpaf.load
RUN a2enmod rpaf
WORKDIR /var/www/html