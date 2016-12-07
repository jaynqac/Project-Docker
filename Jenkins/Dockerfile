FROM myjava:latest
MAINTAINER jaynpham

# adds the key to the container
RUN wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | apt-key add -

# adds pkg
RUN sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.l$

# update local pkg and install jenkins
RUN apt-get update
RUN apt-get install -y jenkins

# start jenkins
CMD service jenkins start && tail -F /var/log/jenkins/error.log
