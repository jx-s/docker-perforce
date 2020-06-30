FROM ambakshi/perforce-base
LABEL maintainer="Fahasiki Jx <sunjianxin0207@gmail.com>"

ARG P4_VERSION

RUN yum clean all --enablerepo='*' \
    && yum clean metadata --enablerepo='*' \
    && yum install --enablerepo=perforce -y helix-p4d helix-cli \
    && yum clean all --enablerepo='*' \
    && rm -rf /var/cache/yum


EXPOSE 1666
ENV NAME p4depot
ENV P4CONFIG .p4config
ENV DATAVOLUME /data
ENV P4PORT 1666
ENV P4USER p4admin
ENV UID 1026
ENV GID 100
VOLUME ["$DATAVOLUME"]

ADD ./p4-users.txt /root/
ADD ./p4-groups.txt /root/
ADD ./p4-protect.txt /root/
ADD ./p4dctl.conf /etc/perforce/
ADD ./p4d.template /etc/perforce/p4dctl.conf.d/
ADD ./setup-perforce.sh /usr/local/bin/
ADD ./run.sh  /

CMD ["/run.sh"]
