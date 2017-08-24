FROM alpine:3.6

LABEL maintainer Matthieu Monnier <matthieu.monnier@enalean.com>

ENV PKGVER="4.4.3"
ENV GOPATH="/srv/go" 
ENV GO_SRC="src/github.com/grafana/grafana"
ENV GF_HOME="/usr/share/grafana"
ENV GF_CONF="/etc/grafana"
ENV GF_DATA="/var/lib/grafana"
ENV GF_LOG="/var/log/grafana"
ENV PATH="$PATH:$GOPATH/bin"
ENV SOURCE="https://github.com/grafana/grafana"

RUN apk add --no-cache --repository \
        # Add edge repository for Go 1.8.1
        http://dl-cdn.alpinelinux.org/alpine/edge/community \
        --virtual .build-deps \
            build-base \
            git \
            go \
            nodejs-current \
            nodejs-current-npm \
            python \
    && mkdir -p ${GOPATH}/src/github.com/grafana ${GF_HOME}/conf ${GF_CONF} \
        ${GF_LOG} ${GF_DATA}/plugins \
    && cd ${GOPATH}/src/github.com/grafana \
    && git clone --depth 1 -b v${PKGVER} ${SOURCE} \
    && cd grafana \
    && go run build.go setup \
    && go run build.go build \
    && npm install -g yarn \
    && yarn install \
    && npm run build \
    && npm uninstall -g yarn \
    && cp ${GOPATH}/${GO_SRC}/bin/grafana-server /usr/bin \
    && cp ${GOPATH}/${GO_SRC}/bin/grafana-cli /usr/bin \
    && cp -a ${GOPATH}/${GO_SRC}/public_gen ${GF_HOME}/public \
    && cp ${GOPATH}/${GO_SRC}/conf/defaults.ini ${GF_HOME}/conf \
    && apk del .build-deps \
    && apk add --no-cache ca-certificates \
    && rm -rf ${GOPATH} /usr/local \
    && find /root /tmp -mindepth 1 -maxdepth 1 -exec rm -rf {} \;

VOLUME [ "/etc/grafana", "/var/log/grafana", "/var/lib/grafana" ]

EXPOSE 3000

WORKDIR /usr/share/grafana

CMD [ "/usr/bin/grafana-server", "-homepath", "/usr/share/grafana", \
    "-config", "/etc/grafana/grafana.ini", "-pidfile", "/run/grafana.pid" ]
