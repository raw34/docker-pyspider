#
# Python Dockerfile
#
#

FROM python:3.6-stretch

MAINTAINER raw34 <raw34@sina.com>

WORKDIR /www

RUN \
    mkdir /root/.ssh \
    mkdir /root/.pip

COPY ./pip.conf /root/.pip/pip.conf
COPY ./pydistutils.cfg /root/.pydistutils.cfg

RUN \
    cp /etc/apt/sources.list /etc/apt/sources.list.bak \
#    && sed -i 's|security.debian.org/debian-security|mirrors.ustc.edu.cn/debian-security|g' /etc/apt/sources.list \
#    && sed -i 's|deb.debian.org|mirrors.ustc.edu.cn|g' /etc/apt/sources.list
#    && sed -i 's|security.debian.org/debian-security|mirrors.tuna.tsinghua.edu.cn/debian-security|g' /etc/apt/sources.list \
#    && sed -i 's|deb.debian.org|mirrors.tuna.tsinghua.edu.cn|g' /etc/apt/sources.list
    && sed -i 's|security.debian.org/debian-security|mirrors.aliyun.com/debian-security|g' /etc/apt/sources.list \
    && sed -i 's|deb.debian.org|mirrors.aliyun.com|g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    libxml2-dev \
    libxslt1-dev \
    phantomjs \
    python-lxml \
    --no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

# Install pyspider
RUN \
    pip install pyspider
