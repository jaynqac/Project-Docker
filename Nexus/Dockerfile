FROM myjava:latest
MAINTAINER jaynpham
#user root

RUN apt-get update -y
RUN apt-get install -y wget
WORKDIR /opt

RUN wget http://download.sonatype.com/nexus/3/nexus-3.0.0-03-unix.tar.gz
RUN tar zxvf nexus-3.0.0-03-unix.tar.gz

ENTRYPOINT ./nexus-3.0.0-03/bin/nexus start && bash

