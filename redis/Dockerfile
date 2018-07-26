FROM ccr.ccs.tencentyun.com/ruan.sheng/base-centos
MAINTAINER ruansheng 825307513@qq.com

RUN yum install -y vim pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel

ADD http://download.redis.io/releases/redis-3.2.9.tar.gz .
RUN tar zxvf redis-3.2.9.tar.gz
RUN mv redis-3.2.9 /usr/local/redis && \
cd /usr/local/redis && make
