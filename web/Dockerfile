FROM php:7.4-apache

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions http \
    pdo_mysql \
    mysqli \
    mbstring \
    json \
    xml \
    zip \
    opcache \
    gd

#копирование скрипта-заглушки для обработки функции php mail
RUN mkdir /var/www/system_dir
COPY mail.php /var/www/system_dir

#добавление директив php.ini
COPY bx.ini /usr/local/etc/php/conf.d/

#создание виртуальных хостов
COPY sites.conf /etc/apache2/sites-available/000-default.conf

#включение mod rewrite-а Apache
RUN ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load

#добавление настроек opcache
COPY opcache.ini /usr/local/etc/php/conf.d/opcache.ini