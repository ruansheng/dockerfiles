FROM ccr.ccs.tencentyun.com/ruan.sheng/base-centos
MAINTAINER ruansheng <825307513@qq.com>

RUN yum install -y pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel curl-devel libxml2-devel m4 autoconf

ADD http://download.icu-project.org/files/icu4c/62.1/icu4c-62_1-src.tgz .
RUN tar xf icu4c-62_1-src.tgz && cd icu/source && ./configure --prefix=/usr/local/icu && make && make install

ADD http://ca1.php.net/distributions/php-7.2.6.tar.gz .
RUN tar zxvf php-7.2.6.tar.gz
RUN mkdir -p /usr/local/php7
RUN cd php-7.2.6 && ./configure --prefix=/usr/local/php7 --enable-fpm --enable-maintainer-zts --with-curl --with-openssl --enable-intl --with-icu-dir=/usr/local/icu --enable-mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd && \
make && make install && cp php.ini-production /usr/local/php7/lib/php.ini && \
cp /usr/local/php7/etc/php-fpm.conf.default /usr/local/php7/etc/php-fpm.conf && \
cp /usr/local/php7/etc/php-fpm.d/www.conf.default /usr/local/php7/etc/php-fpm.d/www.conf

RUN sed -i 's/;pid = run\/php-fpm.pid/pid = run\/php-fpm.pid/' /usr/local/php7/etc/php-fpm.conf
RUN sed -i 's/;error_log = log\/php-fpm.log/error_log = log\/php-fpm.log/' /usr/local/php7/etc/php-fpm.conf

#RUN /usr/local/php7/bin/pecl install redis 
#RUN sed -i '$a extension=redis.so' /usr/local/php7/lib/php.ini
