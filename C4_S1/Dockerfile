FROM ubuntu:22.10

RUN apt-get update && \
    apt-get install -y docker.io && \
    systemctl start docker && \
    systemctl enable docker

RUN apt-get install -y openssh-client openssh-server

COPY sources.list /etc/apt/sources.list

RUN useradd -m -s /bin/bash prueba && \
    echo "prueba:prueba" | chpasswd

RUN service ssh start

CMD ["/usr/sbin/sshd", "-D"]
