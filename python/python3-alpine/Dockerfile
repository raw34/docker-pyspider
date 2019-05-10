#
# Python Dockerfile
#
#

FROM python:3.6-alpine

MAINTAINER raw34 <raw34@sina.com>

RUN \
    mkdir /root/.ssh \
    mkdir /root/.pip

COPY ./pip.conf /root/.pip/pip.conf
COPY ./pydistutils.cfg /root/.pydistutils.cfg

RUN \
    mv /etc/apk/repositories /etc/apk/repositories.bak \
    # echo "http://mirror.tuna.tsinghua.edu.cn/alpine/latest-stable/main/" >> /etc/apk/repositories && \
    # echo "http://mirrors.ustc.edu.cn/alpine/latest-stable/main/" >> /etc/apk/repositories && \
    && echo "http://mirrors.aliyun.com/alpine/latest-stable/main/" >> /etc/apk/repositories

RUN \
    apk add --update \
    curl-dev \
    libxslt-dev \
    libxml2-dev \
    tzdata \
    && rm -rf /var/cache/apk/*

# Install pyspider
RUN \
#    easy_install lxml==3.6.1 \
#    pip install lxml==3.6.1 \
#    pip install scrapy \
#    pip install lxml \
    pip install pyspider
#    easy_install pyspider

# Set timezone
ENV TZ="Asia/Shanghai"

RUN \
    echo "Asia/Shanghai" > /etc/timezone
