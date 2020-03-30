FROM debian:testing

RUN apt-get update && apt-get install -y openssh-server; \
    apt-get -y -q=1 clean; \
    rm -rf /var/lib/apt/lists/*; \
    mkdir /var/run/sshd; \
    echo 'root:THEPASSWORDYOUCREATED' | chpasswd; \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config; \
    sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd;

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
