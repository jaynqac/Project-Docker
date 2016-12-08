FROM ubuntu:latest
MAINTAINER jaynpham

# install wget
RUN apt-get update
RUN apt-get install -y wget

# download java tarball from the internet and store in /opt
WORKDIR /opt
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-put/java/jdk/8u112-b15/jdk-8u112-linux-x64.tar.gz

# extract java
RUN tar zxvf jdk-8u112-linux-x64.tar.gz

# install java
RUN update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_112/bin/java 100
RUN update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_112/bin/javac 100