FROM php:7.1.4-cli

# Install essential dependecies
RUN apt-get update && apt-get -y --no-install-recommends install apt-transport-https

# Install depedencies
RUN echo "deb http://ftp.fr.debian.org/debian sid main" > /etc/apt/sources.list.d/main.list \
    && curl -sL https://deb.nodesource.com/setup_6.x | bash - \
    && apt-get update \
    && apt-get -y --no-install-recommends install \
        curl \
        ca-certificates \
        zlib1g-dev \
        libicu-dev \
        libpcre3-dev \
        git \
        vim \
        bash-completion \
        nano \
        nodejs \
    && docker-php-ext-install \
        zip \
        intl \
    && docker-php-source delete \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

# Install asset manager (npm, node, etc ...)
RUN npm install -g npm gulp gulp-cli less bower bower-shrinkwrap-resolver node-gyp

# Install standard code editor (phpcs, phpms, etc ...)
RUN curl https://raw.githubusercontent.com/jaytaph/SFConsole/master/console_completion.sh > /etc/bash_completion.d/symfony2
RUN curl https://raw.githubusercontent.com/qbbr/symfony-bash-completion/master/composer-autocomplete.bash > /etc/bash_completion.d/composer

ADD bash.bashrc /etc/bash.bashrc
ADD .bashrc /root/.bashrc

RUN composer global require \
    phpunit/phpunit \
    friendsofphp/php-cs-fixer \
    phploc/phploc \
    pdepend/pdepend \
    phpmd/phpmd \
    sebastian/phpcpd \
    escapestudios/symfony2-coding-standard:~2.0 \
    && ln -s /root/.composer/vendor/bin/* /usr/local/bin/

RUN phpcs --config-set installed_paths /root/.composer/vendor/escapestudios/symfony2-coding-standard
RUN phpcs -i

WORKDIR /var/www/project

CMD ["tail", "-f", "/dev/null"]
