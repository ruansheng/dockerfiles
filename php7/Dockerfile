FROM ccr.ccs.tencentyun.com/ruan.sheng/base-centos
MAINTAINER ruansheng <825307513@qq.com>

RUN yum install -y pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel curl-devel libxml2-devel m4 autoconf zip unzip

ADD http://ca1.php.net/distributions/php-7.2.6.tar.gz .
RUN tar zxvf php-7.2.6.tar.gz
RUN mkdir -p /usr/local/php7
RUN cd php-7.2.6 && ./configure --prefix=/usr/local/php7 --enable-fpm --enable-maintainer-zts --enable-mbstring --enable-zip --with-curl --with-openssl --enable-mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd && \
make && make install && cp php.ini-production /usr/local/php7/lib/php.ini && \
cp /usr/local/php7/etc/php-fpm.conf.default /usr/local/php7/etc/php-fpm.conf && \
cp /usr/local/php7/etc/php-fpm.d/www.conf.default /usr/local/php7/etc/php-fpm.d/www.conf

RUN sed -i 's/;pid = run\/php-fpm.pid/pid = run\/php-fpm.pid/' /usr/local/php7/etc/php-fpm.conf
RUN sed -i 's/;error_log = log\/php-fpm.log/error_log = log\/php-fpm.log/' /usr/local/php7/etc/php-fpm.conf

RUN /usr/local/php7/bin/pecl install redis
RUN sed -i '$a extension=redis.so' /usr/local/php7/lib/php.ini

RUN /usr/local/php7/bin/pecl install mongodb
RUN sed -i '$a extension=mongodb.so' /usr/local/php7/lib/php.ini

ENV PATH /usr/local/php7/bin:$PATH

RUN wget https://dl.laravel-china.org/composer.phar -O /usr/local/bin/composer && chmod a+x /usr/local/bin/composer