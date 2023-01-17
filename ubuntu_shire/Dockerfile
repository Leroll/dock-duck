FROM ubuntu:18.04
LABEL maintainer=“Leroll”

COPY ./* /ontech/
RUN cd /ontech \
    # 基础软件
    && sed -i s@/archive.ubuntu.com/@/mirrors.tuna.tsinghua.edu.cn/@g /etc/apt/sources.list \
    && apt-get update && apt-get install -y vim \
    # asr 动态库
    && mv ./lib* /usr/lib/

WORKDIR /ontech/




