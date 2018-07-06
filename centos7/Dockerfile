#
#MAINTAINER 	liyongjian5179 <liyongjian5179@163.com>
# DOCKER-VERSION    1.8.2
#
# Dockerizing CentOS7: Dockerfile for building CentOS images
#
#FROM       centos:7.1.1503
FROM       centos
MAINTAINER liyongjian5179 <liyongjian5179@163.com>

ENV TZ "Asia/Shanghai"
ENV TERM xterm

COPY aliyun-mirror.repo /etc/yum.repos.d/CentOS-Base.repo
COPY aliyun-epel.repo /etc/yum.repos.d/epel.repo

RUN yum install -y curl wget tar bzip2 unzip vim-enhanced passwd sudo yum-utils hostname net-tools rsync man && \
    yum install -y gcc gcc-c++ git mvn make automake cmake patch logrotate python-devel libpng-devel libjpeg-devel && \
    yum install -y --enablerepo=epel pwgen python-pip && \
    yum clean all

RUN pip install supervisor
COPY supervisord.conf /etc/supervisord.conf

RUN mkdir -p /etc/supervisor.conf.d && \
    mkdir -p /var/log/supervisor

#EXPOSE 22

CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]

