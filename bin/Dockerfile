FROM wordpress:cli-php5.6

USER root

RUN echo http://mirror.yandex.ru/mirrors/alpine/v3.4/main > /etc/apk/repositories; \
    echo http://mirror.yandex.ru/mirrors/alpine/v3.4/community >> /etc/apk/repositories

RUN apk --no-cache --update add bash subversion sudo

RUN docker-php-ext-install pdo_mysql

# This allows the script to call sudo without a TTY. Might be better just to run
# wp-cli with "--allow-root" (which is the only reason we run as www-data).
RUN echo "www-data ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

USER www-data

WORKDIR /project
