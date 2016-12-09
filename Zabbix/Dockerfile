FROM ubuntu:xenial
MAINTAINER jaynpham

RUN apt-get update
RUN apt-get install -y wget
RUN apt-get update -y \
&& apt-get install -y debconf-utils \
 apache2 \
 mysql-client \
 php7.0-mysql php7.0-curl php7.0-json php7.0-cgi php7.0 libapache2-mod-php7.0 php7.0-bcmath php7.0-mbstring php7.0-xml

RUN sed -i 's:;date.timezone =:date.timezome = UTC:g' /etc/php/7.0/apache2/php.ini


#RUN DEBIAN_FRONTEND=noninteractive apt-get install -y zabbix-server-mysql zabbix-frontend-php liba

RUN echo 'mysql-server mysql-server/root_password password zabbix' | debconf-set-selections
RUN echo 'mysql-server mysql-server/root_password_again password zabbix' | debconf-set-selections
RUN apt-get install -y mysql-server

WORKDIR /opt
RUN wget http://repo.zabbix.com/zabbix/3.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.2-1+xenial_all.deb
RUN dpkg -i zabbix-release_3.2-1+xenial_all.deb
RUN apt-get update -y
RUN apt-get install -y zabbix-server-mysql zabbix-frontend-php zabbix-agent

RUN service mysql start\
&& mysql -u root -pzabbix -e "CREATE USER zabbix;"\
&& mysql -u root -pzabbix -e "CREATE DATABASE zabbixdb character set utf8 collate utf8_bin;"\
&& mysql -u root -pzabbix -e "GRANT ALL PRIVILEGES on zabbixdb.* to zabbix@localhost identified by 'zabbix';" \
&& mysql -u root -pzabbix -e "FLUSH PRIVILEGES;"

WORKDIR /usr/share/doc/zabbix-server-mysql/

RUN service mysql start \
&& zcat create.sql.gz | mysql -u root -pzabbix zabbixdb

WORKDIR /etc/zabbix/
EXPOSE 8082:80

RUN sed -i  "s/# DBHost=/DBHost=localhost/g" zabbix_server.conf \
&& sed -i "s/DBName=zabbix/DBName=zabbixdb/g" zabbix_server.conf \
&& sed -i  "s/# DBPassword=/DBPassword=zabbix/g" zabbix_server.conf \
&& sed -i "s/#DBPort=/DBPort=3306/g"

RUN service apache2 restart && service zabbix-server restart

ENTRYPOINT service mysql start && service zabbix-server start && service apache2 start && service zabbix-agent start && bash


