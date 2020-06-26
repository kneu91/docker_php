FROM php:7.4-apache
RUN apt-get update && apt-get upgrade -y
RUN docker-php-ext-install mysqli pdo_mysql
RUN a2enmod rewrite

RUN apt-get update &&  apt-get install -y -qq git
# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

#RUN apt-get install -y libfreetype6-dev
#RUN apt-get update -y && apt-get install -y libpng-dev  libfreetype6-dev libjpeg62-turbo-dev zlib1g-dev
#RUN apt-get update && \
#    apt-get install -y \
#        zlib1g-dev
#
#RUN apt-get update && \
#    apt-get install -y -qq git \
#        nano \
#        libjpeg62-turbo-dev \
#        apt-transport-https \
#        libfreetype6-dev \
#        libmcrypt-dev \
#        libpng12-dev \
#RUN docker-php-ext-install gd
#RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
#RUN docker-php-ext-install -j$(nproc) gd
#ustawiamy memlimit
RUN echo 'memory_limit = 512M' >> /usr/local/etc/php/conf.d/docker-php-memlimit.ini;
#ustawiamy katalog domeny
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf
EXPOSE 80