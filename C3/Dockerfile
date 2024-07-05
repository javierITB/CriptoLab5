FROM ubuntu:20.10

RUN sed -i 's|archive.ubuntu.com|old-releases.ubuntu.com|g' /etc/apt/sources.list
RUN sed -i 's|security.ubuntu.com|old-releases.ubuntu.com|g' /etc/apt/sources.list
RUN sed -i '/^# deb-src/s/^# //' /etc/apt/sources.list

RUN apt-get update
RUN apt-get install openssh-server openssh-client zlib1g-dev libssl-dev autoconf automake libtool -y
RUN apt-get install dpkg-dev --fix-missing -y
RUN apt-get source openssh-client

RUN mkdir /var/run/sshd

ENV USERNAME=test
ENV USERHOME=/home/$USERNAME
RUN useradd -m -d $USERHOME $USERNAME
RUN echo 'test:test' | chpasswd

RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
