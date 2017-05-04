FROM hauspie/cgir-base

MAINTAINER michael.hauspie@univ-lille1.fr

RUN apt-get update && apt-get install -y bind9 bind9-host dnsutils

EXPOSE 53/udp 53/tcp

# If you want to rebuild SSH keys, uncomment this
# RUN rm -f /etc/ssh/ssh_host_*
# RUN dpkg-reconfigure openssh-server

# Create bind startup script
RUN mkdir -p /var/run/bind
RUN mkdir /etc/service/bind
RUN /bin/echo -e '#!/bin/sh' > /etc/service/bind/run
RUN /bin/echo -e 'exec /usr/sbin/named -f -c /etc/bind/named.conf' >> /etc/service/bind/run
RUN chown root.root /etc/service/bind/run
RUN chmod 755 /etc/service/bind/run


VOLUME ["/etc/bind"]

