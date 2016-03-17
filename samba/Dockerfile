FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive

VOLUME /srv
VOLUME /etc/samba

RUN apt-get update && \
    C_ALL=C DEBIAN_FRONTEND=noninteractive apt-get install -y samba krb5-config

COPY smb.conf /etc/samba/smb.conf

 # DNS
EXPOSE 53
 # Kerberos
EXPOSE 88
 # End Point Mapper (DCE/RPC Locator Service)
EXPOSE 135
 # NetBIOS Session
EXPOSE 137 138 139
 # LDAP
EXPOSE 389
 # SMB over TCP / CIFS
EXPOSE 445
 # Kerberos Passwort
EXPOSE 464
 # LDAPS (only if "tls enabled = yes")
EXPOSE 636
 # dynamische RPC-Ports
EXPOSE 1024-5000
 # globaler Katalog
EXPOSE 3268
 # globaler Katalog SSL
EXPOSE 3269

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN /usr/sbin/smbd && sleep 10 && smbcontrol smbd shutdown

ENTRYPOINT /usr/sbin/smbd -FSD -d1 --option=workgroup=${workgroup:-workgroup}
