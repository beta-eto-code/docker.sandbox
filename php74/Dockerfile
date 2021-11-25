FROM phpdockerio/php74-fpm:latest

RUN apt-get update \
    && apt-get -y --no-install-recommends install git \
    msmtp stow \
    telnet \
    php7.4-memcached \
    php7.4-memcache \
    php7.4-mbstring \
    php7.4-mysql \
    php7.4-intl \
    php7.4-xdebug \
    php7.4-interbase \
    php7.4-soap \
    php7.4-gd \
    php7.4-imagick \
    php7.4-opcache \
    php7.4-xml \
    php7.4-zip \
    php-pear php-dev libmcrypt-dev gcc make autoconf libc-dev pkg-config \
    && pecl install mcrypt-1.0.3 \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN update-alternatives --set php /usr/bin/php7.4

ADD ./php.ini /etc/php/7.4/fpm/conf.d/90-php.ini
ADD ./php.ini /etc/php/7.4/cli/conf.d/90-php.ini
COPY ./msmtprc /etc/msmtprc
RUN echo 'sendmail_path = "/usr/bin/msmtp -t"' > /etc/php/7.4/cli/conf.d/00-msmtp.ini
RUN echo 'sendmail_path = "/usr/bin/msmtp -t"' > /etc/php/7.4/fpm/conf.d/00-msmtp.ini

RUN usermod -u 1000 www-data

WORKDIR "/var/www/bitrix"

EXPOSE 9000
