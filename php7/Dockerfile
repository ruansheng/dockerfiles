FROM centos:latest
MAINTAINER ruansheng <825307513@qq.com>
RUN yum install -y pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel curl-devel libxml2-devel m4 autoconf

# install supervisor
RUN yum -y install python-setuptools 
RUN easy_install supervisor
RUN echo_supervisord_conf > /etc/supervisord.conf
RUN mkdir /etc/supervisord
RUN sed -i 's/;files = relative\/directory\/*.ini/files = \/etc/supervisord\/*.ini'

ADD http://ca1.php.net/distributions/php-7.2.6.tar.gz .
RUN tar zxvf php-7.2.6.tar.gz
RUN mkdir -p /usr/local/php7
RUN cd php-7.2.6 && ./configure --prefix=/usr/local/php --enable-fpm --with-curl --with-openssl && \
make && make install && cp php.ini-production /usr/local/php/lib/php.ini && \
cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf && \
cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf

RUN sed -i 's/;pid = run\/php-fpm.pid/pid = run\/php-fpm.pid/' /usr/local/php/etc/php-fpm.conf
RUN sed -i 's/;error_log = log\/php-fpm.log/error_log = log\/php-fpm.log/' /usr/local/php/etc/php-fpm.conf

RUN sed -i '$PATH=/usr/local/php/bin:\$PATH\nexport PATH' ~/.bashrc
RUN source ~/.bashrc

#RUN /usr/local/php7/bin/pecl install redis
#RUN sed -i '$a extension=redis.so' /usr/local/php7/lib/php.ini
