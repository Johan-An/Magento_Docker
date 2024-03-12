# Changelog(1.0.0):
# - Update docker base image
# - Add prestige backup logic

FROM registry.cn-hangzhou.aliyuncs.com/mn/magento-app:dev-8.0.0

LABEL maintainer="Sophia Wang <sophia.wang@mobilenowgroup.com>"

#RUN set -xe; \
#    apt-get update -yqq && \
#    pecl channel-update pecl.php.net && \
#    groupadd -g ${PGID} laradock && \
#    useradd -l -u ${PUID} -g laradock -m laradock -G docker_env && \
#    usermod -p "*" laradock -s /bin/bash && \
#    usermod -a -G docker_env www-data
#
#USER laradock

COPY ./ /var/www

#COPY .env.staging /var/www/.env

RUN apt-get update && apt-get install vim -y

WORKDIR /var/www

CMD /opt/startup.sh

EXPOSE 9000 80 81
