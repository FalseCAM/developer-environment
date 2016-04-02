FROM ubuntu:trusty

#VOLUME ["/srv"]
#VOLUME ["/etc/samba"]
#VOLUME ["/var/lib/samba"]

RUN apt-get update && \
    C_ALL=C DEBIAN_FRONTEND=noninteractive apt-get install -y libacl1-dev libattr1-dev samba krb5-config ntp

ENV DEBIAN_FRONTEND noninteractive
ENV SAMBA_DOMAIN example
ENV SAMBA_REALM example.com
ENV SAMBA_HOST_NAME samba
ENV DNS_FORWARDER 8.8.8.8
ENV SAMBA_ADMINPASS secret-PW!

RUN mkdir -p /etc/samba/
#COPY smb.conf /etc/samba/smb.conf
#RUN rm /etc/samba/smb.conf

COPY createdc /usr/local/bin/createdc

# DNS
# Kerberos
# End Point Mapper (DCE/RPC Locator Service)
# NetBIOS Session
# LDAP
# SMB over TCP / CIFS
# Kerberos Passwort
# LDAPS (only if "tls enabled = yes")
# dynamische RPC-Ports
# global Katalog
# global Katalog SSL
EXPOSE 53 88 135 137 138 139 389 445 464 636 3268 3269

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN /usr/local/bin/createdc
#ENTRYPOINT service samba-ad-dc start
ENTRYPOINT ["samba"]
CMD ["-i"]
