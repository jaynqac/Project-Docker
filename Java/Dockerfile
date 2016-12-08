FROM ubuntu:latest
MAINTAINER jaynpham

# install wget
RUN apt-get update
RUN apt-get install -y wget

# download java tarball from the internet and store in /opt
WORKDIR /opt
RUN wget http://download.oracle.com/otn-pub/java/jdk/8u111-b14/jdk-8u111-linux-x64.tar.gz
# extract java
RUN tar -zxvf jdk-8u111-linux-x64.tar.gz

# install java
RUN update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_111/bin/java 100
RUN update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_111/bin/javac 100
