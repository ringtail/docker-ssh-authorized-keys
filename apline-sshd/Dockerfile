FROM alpine:3.4

MAINTAINER ringtail <zhongwei.lzw@alibaba-inc.com>

RUN apk update && \
    apk --no-cache add bash openssh && \
    mkdir -p ~root/.ssh && chmod 700 ~root/.ssh/ && \
    echo -e "Port 22\n" >> /etc/ssh/sshd_config && \
    cp -a /etc/ssh /etc/ssh.cache && \
    rm -rf /var/cache/apk/*

EXPOSE 22

ENV AUTHORIZED_KEYS **None**
ENV DISABLE_HOST_CHECK **None**

COPY entry.sh /entry.sh

RUN chmod +x /entry.sh

ENTRYPOINT ["/entry.sh"]

CMD ["/usr/sbin/sshd", "-D", "-f", "/etc/ssh/sshd_config"]
