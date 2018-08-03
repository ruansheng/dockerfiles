FROM ccr.ccs.tencentyun.com/ruan.sheng/base-centos:latest
MAINTAINER ruansheng 825307513@qq.com

# ADD https://src.fedoraproject.org/repo/pkgs/haproxy/haproxy-1.8.12.tar.gz/sha512/2b782a54988cc88d1af0e5f011af062910e8fac28eab13db7e05a58d0d23961f827da47e3871e8d081f5a2d222588480d81dec2e9f14ec9f54a1c3cb5bf3d56a/haproxy-1.8.12.tar.gz .
COPY haproxy-1.8.12.tar.gz .
RUN tar zxvf haproxy-1.8.12.tar.gz

RUN mkdir -p /usr/local/haproxy
RUN cd haproxy-1.8.12 && make  TARGET=linux3100 CPU=x86_64 PREFIX=/usr/local/haproxy && make install PREFIX=/usr/local/haproxy
COPY haproxy.cfg /usr/local/haproxy/haproxy.cfg