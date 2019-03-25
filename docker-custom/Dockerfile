# DLOG
#
# VERSION               0.1

FROM alpine:3.9
MAINTAINER David Navarro <me@davengeo.com>

ARG VERSION

RUN apk add --no-cache bash gawk sed grep bc coreutils \
    && apk add --no-cache openjdk8-jre wget python3 \
    && wget -q https://bootstrap.pypa.io/get-pip.py \
    && python3 get-pip.py \
    && pip install zk-shell \
    && mkdir -pv /opt \
    && rm -rf get-pip.py \
    && apk del wget

ADD distributedlog-dist-${VERSION}-bin.tar.gz /opt
RUN mv /opt/distributedlog-dist-${VERSION} /opt/distributedlog

COPY scripts/iddle.sh /home/iddle.sh

ENTRYPOINT ["/bin/bash", "/home/iddle.sh"]