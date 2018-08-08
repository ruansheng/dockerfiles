FROM ccr.ccs.tencentyun.com/ruan.sheng/base-centos
MAINTAINER ruansheng 825307513@qq.com

RUN yum install -y pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel

ADD http://nginx.org/download/nginx-1.15.0.tar.gz .
RUN tar zxvf nginx-1.15.0.tar.gz
RUN mkdir -p /usr/local/nginx
RUN cd nginx-1.15.0 && ./configure --prefix=/usr/local/nginx --with-http_ssl_module && make && make install
RUN rm -fv /usr/local/nginx/conf/nginx.conf
RUN mkdir -p /usr/local/nginx/conf/server
COPY proxy_pass.conf /usr/local/nginx/conf/server/proxy_pass.conf
COPY nginx.conf /usr/local/nginx/conf/nginx.conf