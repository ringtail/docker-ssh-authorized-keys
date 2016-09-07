FROM buildpack-deps:jessie

MAINTAINER ringtail <zhongwei.lzw@alibaba-inc.com>

RUN apt-get update -y && \
    apt-get install -y openssh-server && \
    mkdir -p /root/.ssh && chmod 700 /root/.ssh/ && \
    cp -a /etc/ssh /etc/ssh.cache && \
    rm -rf /var/lib/apt/lists/*

EXPOSE 22

ENV AUTHORIZED_KEYS **None**
ENV DISABLE_HOST_CHECK **None**

COPY entry.sh /entry.sh

RUN chmod +x /entry.sh

CMD ["/entry.sh;/usr/sbin/sshd", "-D", "-f", "/etc/ssh/sshd_config"]
