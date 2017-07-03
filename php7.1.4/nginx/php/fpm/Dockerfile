FROM php:7.1.4-fpm

# Add configuration file
COPY etc/php/php.ini /usr/local/etc/php/php.ini
COPY etc/php/php-fpm.conf /usr/local/etc/php/php-fpm.conf
COPY etc/php/pool.d/www.conf /usr/local/etc/php/pool.d/www.conf

# Install necessary dependencies
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    unzip \
    locales \
    cron

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

# Set timezone and locale
RUN rm /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Paris /etc/localtime
RUN "date"
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
    && locale-gen

WORKDIR /var/www/project
