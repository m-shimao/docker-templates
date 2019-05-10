FROM amazonlinux:2-with-sources

ENV container docker

RUN \
  (echo 'include_only=.jp' >>/etc/yum/pluginconf.d/fastestmirror.conf) \
  && yum -y update \
  && yum -y install systemd procps openssh-server passwd sudo vim git \
  && yum clean all \
  && cp -f /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

ENV LANG ja_JP.UTF-8
ENV LC_ALL C

RUN mkdir /var/run/sshd

RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ''

RUN echo "root" | (passwd --stdin root)

RUN \
  sed -ri 's/^#UseDNS yes/UseDNS no/' /etc/ssh/sshd_config \
  && sed -ri 's/^GSSAPIAuthentication yes/GSSAPIAuthentication no/' /etc/ssh/sshd_config \
  && sed -ri 's/^UsePrivilegeSeparation sandbox/UsePrivilegeSeparation no/' /etc/ssh/sshd_config \
  && sed -ri 's/^UsePAM yes/UsePAM no/' /etc/ssh/sshd_config

CMD ["/sbin/init"]
