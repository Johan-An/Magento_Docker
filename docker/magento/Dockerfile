#
#--------------------------------------------------------------------------
# Image Setup
#--------------------------------------------------------------------------
#
# To edit the 'php-fpm' base Image, visit its repository on Github
#    https://github.com/Laradock/php-fpm
#
# To change its version, see the available Tags on the Docker Hub:
#    https://hub.docker.com/r/laradock/php-fpm/tags/
#
# Note: Base Image name format {image-tag}-{php-version}
#

FROM registry.cn-hangzhou.aliyuncs.com/mn/laravel-app:dev-8.0.0
ARG INSTALL_SOAP=false

USER root

RUN apt-get -yqq update

RUN rm /etc/apt/preferences.d/no-debian-php && \
    apt-get -y install libxml2-dev php-soap && \
    docker-php-ext-install soap

RUN apt-get -y install libxslt-dev && \
    docker-php-ext-install xsl

RUN docker-php-ext-install sockets

#RUN set -eux; \
#      curl -L -o  /tmp/libevent.tar.gz https://github.com/libevent/libevent/releases/download/release-2.1.12-stable/libevent-2.1.12-stable.tar.gz   &&\
#      mkdir -p /tmp/libevent-php &&\
#      tar -C /tmp/libevent-php -zxvf /tmp/libevent.tar.gz --strip 1 &&\
#      cd /tmp/libevent-php &&\
#      ./configure --prefix=/usr/local/libevent-2.1.12  &&\
#      make &&\
#      make install &&\
#      rm /tmp/libevent.tar.gz &&\
#      docker-php-ext-install sockets  &&\
#      curl -L -o /tmp/event.tar.gz http://pecl.php.net/get/event-3.0.6.tgz &&\
#      mkdir -p /tmp/event-php &&\
#      tar -C /tmp/event-php -zxvf /tmp/event.tar.gz --strip 1 &&\
#      cd /tmp/event-php &&\
#      phpize &&\
#      ./configure  --with-event-libevent-dir=/usr/local/libevent-2.1.12/ &&\
#      make &&\
#      make install &&\
#      rm /tmp/event.tar.gz &&\
#      docker-php-ext-enable event &&\
#      php -m  | grep -q 'event'

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && \
    php composer-setup.php && \
    php -r "unlink('composer-setup.php');" && \
    mv composer.phar /usr/local/bin/composer