FROM centos:7

MAINTAINER Alexander Usov <errimp@gmail.com>

ENV NGINX_SRC http://nginx.org/packages/centos/7/SRPMS/nginx-1.8.0-1.el7.ngx.src.rpm
ENV NAXSI_VERSION 0.54

RUN yum -y install gcc make openssl-devel patch pcre-devel rpm-build wget zlib-devel

RUN useradd -m builder
USER builder
WORKDIR /home/builder
RUN rpm -i $NGINX_SRC
RUN wget https://github.com/nbs-system/naxsi/archive/${NAXSI_VERSION}.tar.gz -O rpmbuild/SOURCES/${NAXSI_VERSION}.tar.gz
COPY nginx.spec.patch nginx.spec.patch
RUN patch  rpmbuild/SPECS/nginx.spec < nginx.spec.patch

RUN rpmbuild -bb rpmbuild/SPECS/nginx.spec
