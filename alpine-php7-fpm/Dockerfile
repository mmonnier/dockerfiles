FROM alpine:3.6

LABEL maintainer Matthieu Monnier <monnier.matthieu@gmail.com>

RUN apk add --no-cache php7-fpm php7-pdo php7-pdo_mysql php7-mysqli php7-gd \
                       php7-json php7-zlib php7-xml php7-phar php7-openssl \
                       php7-curl php7-opcache php7-ctype php7-apcu \
                       php7-intl php7-bcmath php7-dom php7-mbstring \
                       php7-xmlreader php7-cgi php7-xmlrpc php7-pear

ENTRYPOINT [ "/usr/sbin/php-fpm7", "-F", "-O", "-c" ]
CMD [ "/etc/php7/php-fpm.conf" ]
