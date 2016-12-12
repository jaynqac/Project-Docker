FROM projectdocker_myjava:latest
MAINTAINER jaynpham

RUN apt-get update -y
RUN apt-get install -y wget

WORKDIR /opt
# downloads the latest tar ball from the nexus website
RUN wget http://download.sonatype.com/nexus/3/nexus-3.0.0-03-unix.tar.gz

# extract the tar ball
RUN tar zxvf nexus-3.0.0-03-unix.tar.gz

# starts the nexus service when container is built
ENTRYPOINT ./nexus-3.0.0-03/bin/nexus start && bash

