#
# MAINTAINER liyongjian5179 <liyongjian5179@163.com>
#
# Dockerizing TOMCAT: Dockerfile for building TOMCAT images
#
FROM       liyongjian5179/jdk:1.8.0

MAINTAINER liyongjian5179 <liyongjian5179@163.com>

ENV TOMCAT_MAJOR_VERSION 7
ENV TOMCAT_MINOR_VERSION 7.0.55
ENV CATALINA_HOME /opt/tomcat
ENV APP_DIR ${CATALINA_HOME}/webapps/
ENV JENKINS_HOME /var/jenkins_home
# Install tomcat
# RUN wget -q https://archive.apache.org/dist/tomcat/tomcat-${TOMCAT_MAJOR_VERSION}/v${TOMCAT_MINOR_VERSION}/bin/apache-tomcat-${TOMCAT_MINOR_VERSION}.tar.gz

RUN yum -y install maven  && \
    yum clean all

COPY apache-tomcat-7.0.55.tar.gz /opt/apache-tomcat-7.0.55.tar.gz

WORKDIR /opt

RUN tar zxf apache-tomcat-*.tar.gz && \
    rm apache-tomcat-*.tar.gz && \
    mv apache-tomcat* tomcat
COPY jenkins.war $APP_DIR/jenkins.war
COPY server.xml /opt/tomcat/conf/server.xml
ADD scripts /scripts

EXPOSE 8080 8443
#VOLUME 
VOLUME ["/opt/tomcat/logs"]
VOLUME ["/var/jenkins_home"]

ENTRYPOINT ["/scripts/run"]
