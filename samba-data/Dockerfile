FROM debian:jessie

RUN mkdir -p /srv
RUN mkdir -p /etc/samba

VOLUME /srv
VOLUME /etc/samba

#COPY smb.conf /etc/samba/smb.conf

ENTRYPOINT ["echo", "samba-data"]
