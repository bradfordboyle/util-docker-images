FROM debian:testing
RUN apt-get -y -q=1 update; \
    apt-get -y -q=1 install \
        elfutils \
        git \
        libperl5.30 \
        make \
    ; \
    git clone https://github.com/lvc/vtable-dumper; \
    cd vtable-dumper; \
    make install prefix=/usr/local; \
    git clone https://github.com/lvc/abi-dumper.git; \
    cd abi-dumper; \
    make install prefix=/usr/local; \
    cd ..; \
    rm -rf /usr/local/src/abi-dumper; \
    apt-get -y -q=1 remove git make; \
    apt-get -y -q=1 autoremove; \
    apt-get -y -q=1 clean; \
    rm -rf /var/lib/apt/lists/*

