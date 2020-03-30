FROM debian:testing

RUN apt-get -y -q=1 update; \
    apt-get -y -q=1 install \
        git \
        make \
    ; \
    git clone https://github.com/lvc/abi-compliance-checker.git; \
    cd abi-compliance-checker; \
    make install prefix=/usr/local; \
    cd ..; \
    rm -rf abi-compliance-checker; \
    apt-get -y -q=1 remove git make; \
    apt-get -y -q=1 autoremove; \
    apt-get -y -q=1 clean; \
    rm -rf /var/lib/apt/lists/*