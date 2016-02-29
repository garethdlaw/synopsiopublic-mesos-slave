FROM ubuntu:14.04

RUN apt-get update && \
apt-get install -y curl

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF && \
echo deb http://repos.mesosphere.io/ubuntu trusty main > /etc/apt/sources.list.d/mesosphere.list && \
apt-get update && \
apt-get -y install mesos=0.27.0-0.2.190.ubuntu1404

# http://docs.docker.com/installation/ubuntulinux/
RUN apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
RUN sudo apt-get install apt-transport-https
RUN mkdir -p /etc/apt/sources.list.d
RUN sudo echo deb https://apt.dockerproject.org/repo58 ubuntu-trusty main > /etc/apt/sources.list.d/docker.list
RUN sudo apt-get update
RUN sudo pt-get install -y -q docker-engine=1.8.3


CMD ["/usr/sbin/mesos-slave"]

ENV MESOS_WORK_DIR /tmp/mesos
ENV MESOS_CONTAINERIZERS docker,mesos

# https://mesosphere.github.io/marathon/docs/native-docker.html
ENV MESOS_EXECUTOR_REGISTRATION_TIMEOUT 5mins

VOLUME /tmp/mesos

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
