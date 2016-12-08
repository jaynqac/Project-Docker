FROM ubuntu:latest
MAINTAINER jaynpham

# use root user priviledges
USER root

# set working directory
WORKDIR /opt

RUN apt-get update
RUN apt-get install -y wget

# get bin file
RUN wget https://www.atlassian.com/software/jira/downloads/binary/atlassian-jira-software-7.2.4-x64.bin

# change permissions on binary file
RUN chmod 755 atlassian-jira-software-7.2.4-x64.bin
#COPY reponse.varfile /opt/

# run executable
RUN printf "o\n2\n/opt/atlassian/jira\n/var/atlassian/application-data/jira\n2\n8081\n8005\ny\ni\ny\n" | ./atlassian-jira-software-7.2.4-x64.bin

#EXPOSE 8082

# start service
ENTRYPOINT service jira start && bash


