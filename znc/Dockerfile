FROM ubuntu:trusty

MAINTAINER Alex Crawford

ENV LANG en_US.UTF-8
RUN locale-gen $LANG

RUN apt-get update -q && \
    apt-get install -qy build-essential libperl-dev libssl-dev

ADD http://znc.in/releases/znc-latest.tar.gz /tmp/znc.tar.gz
RUN tar xf /tmp/znc.tar.gz && \
    rm /tmp/znc.tar.gz && \
    mv /znc-* /tmp/znc

RUN cd /tmp/znc && \
    ./configure && \
    make && \
    make install && \
    rm -rf /tmp/znc
RUN useradd --system --user-group znc

VOLUME ["/data"]
EXPOSE 6667

ENTRYPOINT ["znc", "--foreground", "--datadir", "/data"]
