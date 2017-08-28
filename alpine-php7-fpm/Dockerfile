FROM alpine:3.6

MAINTAINER Matthieu Monnier <matthieu.monnier@enalean.com>

RUN apk add --no-cache php7-fpm

ENTRYPOINT [ "/usr/sbin/php-fpm7", "-F", "-O", "-c", "/etc/php7/php-fpm.conf", ]
