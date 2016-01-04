# vim: set ft=dockerfile:
FROM centos:6

MAINTAINER Alexander Usov <errimp@gmail.com>

ENV NGINX_SRC http://nginx.org/packages/centos/6/SRPMS/nginx-1.8.0-1.el6.ngx.src.rpm
ENV NAXSI_VERSION 0.54

# install build dependencies
RUN yum -y install gcc make openssl-devel patch pcre-devel rpm-build tar wget zlib-devel

RUN useradd -m builder
USER builder
WORKDIR /home/builder
COPY nginx.spec.patch nginx.spec.patch
RUN rpm -i $NGINX_SRC \
  && wget https://github.com/nbs-system/naxsi/archive/${NAXSI_VERSION}.tar.gz -O rpmbuild/SOURCES/${NAXSI_VERSION}.tar.gz \
  && patch rpmbuild/SPECS/nginx.spec < nginx.spec.patch \
  && rpmbuild -bb rpmbuild/SPECS/nginx.spec
