FROM hauspie/cgir-base

MAINTAINER michael.hauspie@univ-lille1.fr

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y slapd ldap-utils

EXPOSE 389/tcp


# Create slapd service
RUN mkdir -p /var/run/slapd
RUN mkdir /etc/service/slapd
RUN /bin/echo -e '#!/bin/sh' > /etc/service/slapd/run
RUN /bin/echo -e 'exec slapd -h "ldap:/// ldapi:///" -d 32768 -u openldap -g openldap -F /etc/ldap/slapd.d' >> /etc/service/slapd/run
RUN chown root.root /etc/service/slapd/run
RUN chmod 755 /etc/service/slapd/run


VOLUME ["/etc/ldap"]
