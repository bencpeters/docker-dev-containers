FROM devbase
MAINTAINER Ben Peters

WORKDIR /home/benpeters
USER benpeters
RUN mkdir .ssh; chmod 700 .ssh
ADD authorized_keys /home/benpeters/.ssh/authorized_keys

USER root

RUN chown benpeters:benpeters /home/benpeters/.ssh/authorized_keys
RUN apt-get install -y openssh-server htop screen

RUN mkdir /var/run/sshd
ADD ssh_config /etc/ssh/ssh_config
ENTRYPOINT /usr/sbin/sshd -D
EXPOSE 22
