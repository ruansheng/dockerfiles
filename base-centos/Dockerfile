FROM centos
MAINTAINER ruansheng 825307513@qq.com

# set time zone
RUN /usr/bin/cp -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

# install supervisor
RUN yum -y install epel-release
RUN yum -y install supervisor
RUN mkdir -p /var/log/supervisor
RUN sed -i "s/nodaemon=false/nodaemon=true/g" /etc/supervisord.conf

# install vim
RUN yum -y install vim git

# install tcpdump
RUN yum -y install tcpdump

# install net-tools ifconfig
RUN yum -y install net-tools

# install strace
RUN yum -y install strace

# install make
RUN yum -y install gcc gcc-c++ make m4 autoconf

## install zip unzip
RUN yum -y install zip unzip