FROM ubuntu:12.04
MAINTAINER Francesco Sullo, sullof@sullof.com, http://sullof.com

ENV http_proxy http://172.21.81.28:6588
ENV https_proxy http://172.21.81.28:6588

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get -y upgrade
RUN apt-get install -y openssh-server python-setuptools && /usr/bin/easy_install supervisor

ADD adds/authorized_keys /authorized_keys
ADD adds/configure.sh /configure.sh
RUN bin/bash /configure.sh && rm /configure.sh

ADD adds/supervisord.conf /etc/supervisord.conf

EXPOSE 22

CMD ["/usr/local/bin/supervisord","-n"]

