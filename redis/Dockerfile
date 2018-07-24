FROM centos
MAINTAINER ruansheng 825307513@qq.com

RUN /usr/bin/cp -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

RUN yum install -y vim pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel

ADD http://download.redis.io/releases/redis-3.2.9.tar.gz .
RUN tar zxvf redis-3.2.9.tar.gz
RUN mv redis-3.2.9 /usr/local/redis && \
cd /usr/local/redis && make
EXPOSE 6379
