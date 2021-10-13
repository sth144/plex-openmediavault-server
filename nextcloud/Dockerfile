FROM nextcloud:latest

RUN apt-get update
RUN apt-get install -y libsmbclient-dev smbclient
RUN pecl install smbclient
RUN echo "extension-smbclient.so" > /usr/local/etc/php/conf.d/docker-php-ext-smbclient.ini

