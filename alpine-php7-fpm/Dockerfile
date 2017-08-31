FROM alpine:3.6

LABEL maintainer Matthieu Monnier <monnier.matthieu@gmail.com>

RUN apk add --no-cache php7-fpm php7-pdo_mysql php7-mysqli

ENTRYPOINT [ "/usr/sbin/php-fpm7", "-F", "-O", "-c" ]
CMD [ "/etc/php7/php-fpm.conf" ]
