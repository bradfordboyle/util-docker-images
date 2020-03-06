FROM alpine:3.10

ENV _AUTOCONF_GPG_KEY A7A16B4A2527436A
ENV _AUTOCONF_VERSION 2.69

RUN apk add --no-cache --virtual .build-deps \
        gcc \
        gnupg \
        m4 \
        make \
        perl \
        tar \
    ; \
    \
    version="$_AUTOCONF_VERSION"; \
    wget -O autoconf.tar.gz "http://ftp.gnu.org/gnu/autoconf/autoconf-$version.tar.gz"; \
    wget -O autoconf.tar.gz.sig "http://ftp.gnu.org/gnu/autoconf/autoconf-$version.tar.gz.sig"; \
    export GNUPGHOME="$(mktemp -d)"; \
    gpg --batch --keyserver ha.pool.sks-keyservers.net --recv-keys "$_AUTOCONF_GPG_KEY"; \
    gpg --batch --verify autoconf.tar.gz.sig autoconf.tar.gz; \
    gpgconf --kill all; \
    rm autoconf.tar.gz.sig; \
    rm -rf "$GNUPGHOME"; \
    mkdir -p /usr/src/autoconf; \
    tar \
        --extract \
        --file=autoconf.tar.gz \
        --strip-components=1 \
        --directory=/usr/src/autoconf \
    ; \
    rm autoconf.tar.gz; \
    cd /usr/src/autoconf; \
    ./configure; \
    make -j "$(nproc)"; \
    make install; \
    cd /; \
    rm -r /usr/src/autoconf; \
