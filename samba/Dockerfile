FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive

VOLUME /srv

RUN apt-get update && \
    C_ALL=C DEBIAN_FRONTEND=noninteractive apt-get install -y samba krb5-config

# copy default config lam
COPY smb.conf /etc/samba/smb.conf

EXPOSE 137 138 139 445

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN /usr/sbin/smbd && sleep 10 && smbcontrol smbd shutdown

ENTRYPOINT /usr/sbin/smbd -FSD -d1 --option=workgroup=${workgroup:-workgroup}
