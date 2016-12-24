# centos
基础镜像的parent（父）镜像是从官方Dockerhub中pull下来的，centos:7.1.1503。

    基础镜像主要完成,安装必须的软件包和常用命令工具

如何构建基础镜像

git clone https://github.com/liyongjian5179/centos.git
cd centos
docker build -t csphere/centos:7 .

如何使用基础镜像

docker run -d --name base csphere/centos:7
如何基于基础镜像构建中间件镜像

    创建并编写Dockerfile文件，内容大概如下：

FROM csphere/centos:7
MAINTAINER Carson,C.J.Zeong <zcy@nicescale.com>
RUN yum -y install nginx
...
CMD ["nginx"]

    构建镜像

docker build -t csphere/nginx . 
