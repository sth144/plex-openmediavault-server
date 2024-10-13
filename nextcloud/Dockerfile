FROM nextcloud:23.0.12

RUN apt-get update
RUN apt install -y smbclient libsmbclient-dev && rm -rf /var/lib/apt/lists/*
#RUN apt-get install -y php-smbclient libsmbclient-dev smbclient libsmbclient
RUN pecl install smbclient
#RUN echo "extension-smbclient.so" > /usr/local/etc/php/conf.d/docker-php-ext-smbclient.ini
RUN docker-php-ext-enable smbclient
