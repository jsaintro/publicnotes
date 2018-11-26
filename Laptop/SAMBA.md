## Fix for the SAMBA share on the RT-AC1900

1. install samba client

        apt install smbclient

2. Revert to old authentication method

        vi /etc/samba/smb.conf
        [global]
        # Fix for Asus RT-AC1900 samba share
           client NTLMv2 auth = no
           client use spnego = no

3. Test


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg4NTM0NjM4OSw0MzYyNTY2MDRdfQ==
-->