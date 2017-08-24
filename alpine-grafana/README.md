[![Build Status](https://travis-ci.org/mmonnier/docker-alpine-grafana.svg?branch=master)](https://travis-ci.org/mmonnier/docker-alpine-grafana)
[![Docker Repository on Quay](https://quay.io/repository/mmonnier/docker-alpine-grafana/status "Docker Repository on Quay")](https://quay.io/repository/mmonnier/docker-alpine-grafana)
[![Docker Stars](https://img.shields.io/docker/stars/_/ubuntu.svg?style=flat-square)](https://hub.docker.com/r/mmonnier/alpine-grafana)
[![Docker Pulls](https://img.shields.io/docker/pulls/mashape/kong.svg?style=flat-square)](https://hub.docker.com/r/mmonnier/alpine-grafana)

docker-alpine-grafana
=====================

This Dockerfile builds a Docker image on Alpine Linux with Grafana.

Build your container
--------------------
* Clone this repo and build
```
# build -t alpine-grafana:4.4.2-r0 .
```

Running your container
----------------------

* Don't forget to copy the **grafana.ini** file in your ${VOLUME_1}
```
# docker run 
    -d
    --name=alpine-grafana
    -v ${VOLUME_1}:/etc/grafana \
    -v ${VOLUME_2}:/var/lig/grafana \
    -v ${VOLUME_3}:/var/log/grafana \
    -p 3000:3000 \
    alpine-grafana:4.4.2-r0
```

* The size of image
```
# docker images
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
alpine-grafana                    4.4.2-r0            a3459f70f590        2 minutes ago       83 MB
```
