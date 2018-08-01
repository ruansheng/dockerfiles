FROM ccr.ccs.tencentyun.com/ruan.sheng/nginx-php7:latest
MAINTAINER ruansheng <825307513@qq.com>

RUN yum -y install graphviz

RUN /usr/local/php7/bin/pecl install redis
RUN sed -i '$a extension=redis.so' /usr/local/php7/lib/php.ini