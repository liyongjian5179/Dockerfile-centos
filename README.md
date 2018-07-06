# centos
基础镜像的parent（父）镜像是从官方Dockerhub中pull下来的，centos:latest。

    基础镜像主要完成,安装必须的软件包和常用命令工具

如何构建基础镜像

git clone https://github.com/liyongjian5179/centos.git
cd centos/centos7
docker build -t liyongjian5179/centos:7 .

如何使用基础镜像

docker run -d --name base liyongjian5179/centos:7
如何基于基础镜像构建中间件镜像

    创建并编写Dockerfile文件，内容大概如下：

FROM liyongjian5179/centos:7  
MAINTAINER liyongjian5179 <liyongjian5179@163.com>  
RUN yum -y install nginx  
...  
CMD ["nginx"]

    构建镜像

docker build -t liyongjian5179/nginx . 
