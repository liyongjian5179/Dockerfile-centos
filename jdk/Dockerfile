#
# MAINTAINER liyongjian5179 <liyongjian5179@163.com>
#
# Dockerizing jdk: Dockerfile for building jdk images
#
FROM       liyongjian5179/centos:7
MAINTAINER liyongjian5179 <liyongjian5179@163.com>

ENV JAVA_VERSION 1.8.0
ENV JDK_HOME /usr/lib/jvm/java-1.8.0-openjdk

# Install jdk
RUN yum -y install java-${JAVA_VERSION}-openjdk java-${JAVA_VERSION}-openjdk-devel && \
    yum clean all
