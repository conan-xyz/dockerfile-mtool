FROM ubuntu:18.04

LABEL maintainer="PlatON MTool Docker Maintainers <golang.py@gmail.com>"

ENV MTOOL mtool-client
ENV JDK_DIR jdk1.8.0_221
ENV JDK_NAME jdk-8u221-linux-x64
ENV MTOOL_DIR /root/${MTOOL}
ENV JAVA_HOME /root/${JDK_DIR}
ENV JRE_HOME ${JAVA_HOME}/jre
ENV CLASS_PATH .:${JAVA_HOME}/lib/dt.jar:${JAVA_HOME}/lib/tools.jar:$JRE_HOME/lib
ENV PATH $PATH:${JAVA_HOME}/bin:$JRE_HOME/bin
ENV LANG C.UTF-8

WORKDIR /root

RUN set -eux \
    && apt update \
    && apt install -y wget unzip sudo \
    && wget http://47.91.153.183/third-tools/${JDK_NAME}.tar.gz \
    && wget http://download.alaya.network/alaya/mtool/linux/0.15.0/${MTOOL}.zip \
    && unzip ${MTOOL}.zip \
    && ln -sf ${MTOOL_DIR}/bin/mtool-client /usr/bin/mtool-client \
    && tar -xzvf ${JDK_NAME}.tar.gz \
    && mkdir -pv ca

STOPSIGNAL SIGTERM

CMD [ "bash" ]