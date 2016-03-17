# samba
Docker Container for Samba Domain Controller

Log into docker
	> docker exec -it samba bash

Remove old configuration
	> rm /etc/samba/smb.conf

Configurate Samba
	> samba-tool domain provision --use-rfc2307 --interactive --use-ntvfs

Realm
	> example.com
