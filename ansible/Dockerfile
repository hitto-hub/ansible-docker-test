FROM ubuntu:latest

RUN apt-get update && apt-get install -y \
    openssh-server \
    python3 \
    python3-pip \
	sshpass \
	iputils-ping \
	&& apt-get clean

RUN pip3 install --break-system-packages ansible

RUN mkdir /var/run/sshd

CMD ["/usr/sbin/sshd", "-D"]
