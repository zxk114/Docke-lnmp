#
# Dockerfile for building v2ray images
# 
FROM v2ray/official
MAINTAINER zxk114 <zxk114@126.com>

ENV TZ "Asia/Shanghai"

RUN yum -y update && \
    yum install -y unzip && \
    yum clean all

RUN rm -f /etc/localtime \
	&& ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
	&& date -R \
	&& bash <(curl -L -s https://install.direct/go.sh) \
    && mkdir /var/log/v2ray \
	&& mkdir /etc/v2ray \
	&& chmod 777 /usr/bin/v2ray/v2ray \
	&& chmod -R 777 /var/log/v2ray \
	&& chmod -R 777 /etc/v2ray \

ADD conf/config.json /etc/v2ray/

EXPOSE 12580

#启动nginx
ENTRYPOINT ["/usr/local/bin/v2ray", "-g", "daemon off;"]
