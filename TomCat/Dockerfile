FROM projectdocker_myjava:latest
MAINTAINER jaynpham

RUN apt-get update && apt-get install -y wget
WORKDIR /opt/

### download and extract TomCat tarball
RUN wget http://apache.mirror.anlx.net/tomcat/tomcat-9/v9.0.0.M13/bin/apache-tomcat-9.0.0.M13.tar.gz
RUN tar zxvf apache-tomcat-9.0.0.M13.tar.gz

### set up a tomcat user
RUN useradd -s /sbin/nologin -d /opt/tomcat/temp tomcat
#WORKDIR /opt/tomcat
RUN chown -R tomcat:tomcat apache-tomcat-9.0.0.M13
RUN chmod -R 755 apache-tomcat-9.0.0.M13

### tomcat configuration
#RUN sed -i 's:port="8080": port="8110":g' apache-tomcat-9.0.0.M13/conf/server.xml
#RUN sed -i 's:<param-value>false:<param-value>true:g' apache-tomcat-9.0.0.M13/conf/web.xml
#RUN sed -i 's:<Context>:<Context reloadable="true">:g' apache-tomcat-9.0.0.M13/conf/context.xml

RUN echo "export JAVA_HOME=/opt/jdk1.8.0_112" >> /etc/profile

WORKDIR /opt/apache-tomcat-9.0.0.M13/bin/
RUN chmod uga+x *.sh
ENTRYPOINT ./startup.sh && bash








