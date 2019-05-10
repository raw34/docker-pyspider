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
    fontconfig-dev \
    g++ \
    libressl-dev \
    libxslt-dev \
    libxml2-dev \
    musl-dev \
    python3-dev \
    tzdata \
    wget \
    && rm -rf /var/cache/apk/*

# Install phantomjs
ENV PHANTOMJS_VERSION=2.11

RUN \
  mkdir -p /usr/share \
  && cd /usr/share \
  && wget https://github.com/Overbryd/docker-phantomjs-alpine/releases/download/${PHANTOMJS_VERSION}/phantomjs-alpine-x86_64.tar.bz2 \
  && tar xjf phantomjs-alpine-x86_64.tar.bz2 \
  && ln -s /usr/share/phantomjs/phantomjs /usr/bin/phantomjs \
  && phantomjs --version \
  && rm -rf /usr/share/phantomjs-alpine-x86_64.tar.bz2

# Install pyspider
RUN \
    pip install wsgidav==2.4.1 \
    && pip install pyspider \
    && rm -rf ~/.cache/pip/*

# Set timezone
ENV TZ="Asia/Shanghai"

RUN \
    echo "Asia/Shanghai" > /etc/timezone

EXPOSE 5000

CMD ["pyspider"]
