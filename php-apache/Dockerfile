FROM php:8.1-apache
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli && docker-php-ext-install pdo pdo_mysql  && docker-php-ext-enable pdo pdo_mysql
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y \
        libapache2-mod-rpaf \
        libzip-dev \
        zip \
        && docker-php-ext-install zip

RUN echo "LoadModule rpaf_module /usr/lib/apache2/modules/mod_rpaf.so" > /etc/apache2/mods-available/rpaf.load
RUN echo -e "<IfModule mod_rpaf.c>\n    RPAF_Enable             On\n    RPAF_Header             X-Real-Ip\n    RPAF_ProxyIPs           127.0.0.1\n    RPAF_SetHostName        On\n    RPAF_SetHTTPS           On\n    RPAF_SetPort            On\n</IfModule>" > /etc/apache2/mods-available/rpaf.conf
RUN a2enmod rpaf
WORKDIR /var/www/html