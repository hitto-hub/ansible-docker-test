FROM ubuntu:latest

RUN apt-get update && apt-get install -y --no-install-recommends \
    openssh-server sudo python3 python3-pip && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    echo "UsePAM yes" >> /etc/ssh/sshd_config

RUN useradd -ms /bin/bash ansible && echo "ansible:password" | chpasswd && adduser ansible sudo

RUN mkdir /var/run/sshd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
