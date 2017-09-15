FROM alpine:3.6

LABEL maintainer Matthieu Monnier <matthieu.monnier@enalean.com>

RUN apk add --no-cache nginx

RUN sed -i 's/error_log.*/error_log\ \/dev\/stderr\ warn;/g' \
	/etc/nginx/nginx.conf && \
	sed -i 's/access_log.*/access_log\ \/dev\/stdout\ combined;/g' \
	/etc/nginx/nginx.conf

ENTRYPOINT [ "/usr/sbin/nginx", "-g", "pid /run/nginx.pid; daemon off;", "-c" ]
CMD [ "/etc/nginx/nginx.conf" ]
