FROM centos:latest
MAINTAINER ruansheng <825307513@qq.com>
RUN yum install -y pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel curl-devel libxml2-devel m4 autoconf
ADD http://ca1.php.net/distributions/php-7.2.6.tar.gz .
RUN tar zxvf php-7.2.6.tar.gz
RUN mkdir -p /usr/local/php7
RUN cd php-7.2.6 && ./configure --prefix=/usr/local/php7 --enable-fpm --with-curl --with-openssl && \
make && make install && cp php.ini-production /usr/local/php7/lib/php.ini && \
cp /usr/local/php7/etc/php-fpm.conf.default /usr/local/php7/etc/php-fpm.conf && \
cp /usr/local/php7/etc/php-fpm.d/www.conf.default /usr/local/php7/etc/php-fpm.d/www.conf

RUN sed -i '$aPATH=/usr/local/php7/bin:\$PATH\nexport PATH' ~/.bashrc
RUN source ~/.bashrc

RUN /usr/local/php7/bin/pecl install redis
RUN sed -i '$a extension=redis.so' /usr/local/php7/lib/php.ini
