FROM ubuntu:xenial
MAINTAINER jaynpham

RUN apt-get update
RUN apt-get install -y wget

# sets the automated answers for the installation wizard 
# inserts the answers into debconf-set-selections
RUN echo "postfix postfix/main_mailer_type string Internet site" | debconf-set-selections
RUN echo "postfix postfix/mailname string ip-172-31-7-135.eu-west-1.compute.internal" | debconf-set-selections

RUN debconf-set-selections preseed.txt
# sets the installation wizard to run noninteractively 
RUN DEBIAN_FRONTEND=noninteractive apt-get install -q -y postfix

# sets the answers for the post fix configuration
RUN postconf -e myhostname="ip-172-31-7-135.eu-west-1.compute.internal"
RUN postconf -e mydestination="ip-172-31-7-135.eu-west-1.compute.internal, ip-172-31-7-135.eu-west-1.compute.internal, localhost.eu-west-1.compute.internal, localhost"
RUN postconf -e mail_spool_directory="/var/spool/mail/"
RUN postconf -e mailbox_command=""

# adds user ubuntu 
RUN useradd -s /bin/bash ubuntu
RUN mkdir /var/spool/mail/ubuntu
RUN chown ubuntu:mail /var/spool/mail/ubuntu

ADD etc-aliases.txt /etc/aliases
RUN chown root:root /etc/aliases
RUN newaliases

RUN apt-get install -q -y syslog-ng

EXPOSE 25

# starts the service when container is built
ENTRYPOINT ["sh", "-c", "service syslog-ng start ; service postfix start ; tail -F /var/log/mail.log"]
